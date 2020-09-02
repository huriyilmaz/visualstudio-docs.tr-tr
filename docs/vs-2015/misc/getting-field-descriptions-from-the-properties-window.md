---
title: Özellikler penceresinden alan açıklamalarını alma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703977"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Özellikler penceresinden alan açıklamalarını alma
**Özellikler** penceresinin alt kısmında, bir açıklama alanı seçili özellik alanı ile ilgili bilgileri görüntüler. Bu özellik varsayılan olarak açıktır. Açıklama alanını gizlemek istiyorsanız, **Özellikler** penceresine sağ tıklayın ve **Açıklama**' ya tıklayın. Bunun yapılması, Menü penceresindeki **Açıklama** başlığının yanındaki onay işaretini de kaldırır. **Açıklamayı** tekrar açmak için aynı adımları izleyerek alanı yeniden görüntüleyebilirsiniz.  
  
 Açıklama alanındaki bilgiler öğesinden gelir <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo> . Her yöntem, arabirim, coclass, ve benzeri, tür kitaplığında yerelleştirilmemiş bir `helpstring` özniteliğe sahip olabilir. **Özellikler** penceresi öğesinden dize alır <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .  
  
### <a name="to-specify-localized-help-strings"></a>Yerelleştirilmiş Yardım dizelerini belirtmek için  
  
1. `helpstringdll`Özniteliği tür kitaplığı () içindeki kitaplık ifadesine ekleyin `typelib` .  
  
   > [!NOTE]
   > Tür kitaplığı bir nesne kitaplığı (. olb) dosyasında ise bu adım isteğe bağlıdır.  
  
2. `helpstringcontext`Dizelerin özniteliklerini belirtin. Öznitelikleri de belirtebilirsiniz `helpstring` .  
  
    Bu öznitelikler, `helpfile` `helpcontext` gerçek. chm dosyası yardım konularında yer alan ve özniteliklerinden farklıdır.  
  
   Vurgulanan Özellik adı için görüntülenecek açıklama bilgilerini almak için, **Özellikler** penceresi <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> Seçili olan özelliği çağırır ve `lcid` çıktı dizesi için istenen özniteliği belirterek. Dahili olarak, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> özniteliğinde belirtilen. dll dosyasını bulur `helpstringdll` ve `DLLGetDocumentation` belirtilen bağlam ve özniteliğe sahip bu. dll dosyasında çağırır `lcid` .  
  
   İmzası ve uygulanması `DLLGetDocumentation` şunlardır:  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 `DLLGetDocumentation`İşlev, DLL için. def dosyasında tanımlanmış bir dışarı aktarma olmalıdır.  
  
 Dahili olarak, aslında DLL olan bir. olb dosyası oluşturulur. Bu DLL, bir kaynak, tür kitaplığı (. tlb) dosyası ve bir tane aktarılmış işlevi içerir `DLLGetDocumentation` .  
  
 . Olb dosyalarında, `helpstringdll` . tlb dosyasının kendisini içeren dosya olduğu için özniteliği isteğe bağlıdır.  
  
 **Açıklamalar** bölmesinde gösterilecek dizeleri almak için, bu nedenle yapmanız gereken en düşük değer `helpstring` tür kitaplığında özniteliği belirtmektir. Bu dizelerin yerelleştirilmesi istiyorsanız, `helpstringdll` (isteğe bağlı) özniteliğini ve `helpstringcontext` (gerekli) özniteliğini belirtmeniz ve uygulamanız gerekir `DLLGetDocumentation` .  
  
 IDL 'nin özniteliği ve ile yerelleştirilmiş bilgileri alınırken uygulanması gereken ek arabirimler yoktur `helpstringcontext` `DLLGetDocumentation` .  
  
 Yerelleştirilmiş adı ve bir özelliğin açıklamasını elde etmenin bir başka yolu da uygulamadır <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> . Bu yöntemin uygulanmasıyla ilgili daha fazla bilgi için bkz. [Özellikler penceresi alanları ve arabirimleri](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Özellikler penceresi alanları ve arabirimleri](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Özellikleri genişletme](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [HelpString](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [HelpContext](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [HelpFile](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)