---
title: 排序屬性範例 （VC + +） |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Sort property [ADO], VC++ example
ms.assetid: 58199284-747b-4312-b97f-797ee7bd4435
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a2092b830501ca22b28e867090623a4343f27eca
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2019
ms.locfileid: "67930962"
---
# <a name="sort-property-example-vc"></a>Sort 屬性範例 (VC++)
這個範例會使用[資料錄集](../../../ado/reference/ado-api/recordset-object-ado.md)物件的[排序](../../../ado/reference/ado-api/sort-property.md)屬性，以重新排序的資料列**資料錄集**衍生自***作者***資料表**Pubs**資料庫。 次要的公用程式常式會列印每個資料列。  
  
```  
// SortPropertyExample.cpp  
// compile with: /EHsc  
#import "msado15.dll" no_namespace rename("EOF", "EndOfFile")  
  
#include <ole2.h>  
#include <stdio.h>  
#include <conio.h>  
  
// Function declarations  
inline void TESTHR(HRESULT x) { if FAILED(x) _com_issue_error(x); };  
void SortX();  
void SortXprint(_bstr_t title, _RecordsetPtr rstp);  
void PrintProviderError(_ConnectionPtr pConnection);  
void PrintComError(_com_error &e);  
  
int main() {  
   if ( FAILED(::CoInitialize(NULL)) )  
      return -1;  
   SortX();  
   ::CoUninitialize();  
}  
  
void SortX() {  
   // Initialize pointers on define. These are in the ADODB::  namespace.  
   _ConnectionPtr pConnection = NULL;  
   _RecordsetPtr pRstAuthors = NULL;  
  
   // Define string variables.  
   _bstr_t strCnn("Provider='sqloledb'; Data Source='My_Data_Source'; Initial Catalog='pubs'; Integrated Security='SSPI';");  
  
   try {  
      TESTHR(pConnection.CreateInstance(__uuidof(Connection)));  
      TESTHR(pRstAuthors.CreateInstance(__uuidof(Recordset)));  
  
      pRstAuthors->CursorLocation = adUseClient;  
      pConnection->Open (strCnn, "", "", adConnectUnspecified);  
      pRstAuthors->Open("SELECT * FROM authors",  
         _variant_t((IDispatch *) pConnection),  
         adOpenStatic, adLockReadOnly, adCmdText);  
  
      SortXprint("    Initial Order    ", pRstAuthors);  
  
      pRstAuthors->Sort = "au_lname ASC, au_fname ASC";  
      SortXprint("Last Name Ascending", pRstAuthors);  
  
      pRstAuthors->Sort = "au_lname DESC, au_fname ASC";  
      SortXprint("Last Name Descending", pRstAuthors);  
   }  
   catch(_com_error &e) {  
      PrintProviderError(pConnection);  
      PrintComError(e);  
   }  
  
   // Clean up objects before exit.  
   if (pRstAuthors)  
      if (pRstAuthors->State == adStateOpen)  
         pRstAuthors->Close();  
   if (pConnection)  
      if (pConnection->State == adStateOpen)  
         pConnection->Close();  
}  
  
// This is the secondary utility routine that prints   
// the given title, and the contents of the specified Recordset.  
void SortXprint(_bstr_t title, _RecordsetPtr rstp) {  
   printf("---------------%s---------------\n", (LPCSTR)title);  
   printf("First Name  Last Name\n"  
      "---------------------------------------------------\n");  
   rstp->MoveFirst();  
   while (!(rstp->EndOfFile)) {  
      _bstr_t aufname;  
      _bstr_t aulname;  
      aufname = rstp->GetFields()->GetItem("au_fname")->Value;  
      aulname = rstp->GetFields()->GetItem("au_lname")->Value,  
         printf("%s    %s\n",(LPCSTR) aufname, (LPCSTR) aulname);  
      rstp->MoveNext();  
   }  
}  
  
void PrintProviderError(_ConnectionPtr pConnection) {  
   // Print Provider Errors from Connection object.  
   // pErr is a record object in the Connection's Error collection.  
   ErrorPtr pErr = NULL;  
  
   if ( (pConnection->Errors->Count) > 0) {  
      long nCount = pConnection->Errors->Count;  
      // Collection ranges from 0 to nCount -1.  
      for ( long i = 0 ; i < nCount ; i++ ) {  
         pErr = pConnection->Errors->GetItem(i);  
         printf("Error number: %x\t%s\n", pErr->Number, (LPCSTR) pErr->Description);  
      }  
   }  
}  
  
void PrintComError(_com_error &e) {  
   _bstr_t bstrSource(e.Source());  
   _bstr_t bstrDescription(e.Description());  
  
   // Print Com errors.    
   printf("Error\n");  
   printf("\tCode = %08lx\n", e.Error());  
   printf("\tCode meaning = %s\n", e.ErrorMessage());  
   printf("\tSource = %s\n", (LPCSTR) bstrSource);  
   printf("\tDescription = %s\n", (LPCSTR) bstrDescription);  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [資料錄集物件 (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [Sort 屬性](../../../ado/reference/ado-api/sort-property.md)
