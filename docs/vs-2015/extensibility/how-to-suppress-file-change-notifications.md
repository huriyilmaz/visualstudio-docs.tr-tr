---
title: 'Nasıl yapılır: dosya değişikliği bildirimlerini gizleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - suppress file change notification
ms.assetid: 891c1eb4-f6d0-4073-8df0-2859dbd417ca
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3f045175eae165b75a887ada2716b19f34fc228b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204074"
---
# <a name="how-to-suppress-file-change-notifications"></a>Nasıl Yapılır: Dosya Değişiklik Bildirimlerini Gizleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Metin arabelleğini temsil eden fiziksel dosya değiştirildiğinde, **aşağıdaki öğelerde yapılan değişiklikleri kaydetmek istiyor musunuz?** iletisini içeren bir iletişim kutusu görüntülenir. Bu dosya değişiklik bildirimi olarak bilinir. Ancak, çok sayıda değişiklik dosyaya ulaşıyorsa, bu iletişim kutusu tekrar tekrar  
  
 Aşağıdaki yordamı kullanarak bu iletişim kutusunu program aracılığıyla gizleyebilirsiniz. Bunu yaparak bir dosyayı hemen yeniden yükleyebilirsiniz. böylece, kullanıcıdan her seferinde değişiklikleri kaydetmesini istemek zorunda kalmadan.  
  
### <a name="to-suppress-file-change-notification"></a>Dosya değişikliği bildirimini gizlemek için  
  
1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsRunningDocumentTable.FindAndLockDocument%2A>Hangi metin arabelleği nesnesinin açık dosyanız ile ilişkilendirildiğini belirleyen yöntemi çağırın.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl> <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> (Belge verileri) nesnesinden arayüzü elde ederek ve sonra <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> metodunu `fIgnore` olarak ayarlanmış şekilde uygulayarak, dosya değişikliklerinin izlenmesini yoksaymak için bellekteki nesneyi doğrudan yönlendirin `true` .  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Bellek içi <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesneyi dosya değişiklikleriyle (örneğin, bileşeninizdeki bir alan eklendiğinde) güncelleştirmek için ve arabirimlerinde Yöntemleri çağırın.  
  
4. Kullanıcının sürmekte olan bekleyen düzenlemeleri dikkate almadan diskteki dosyayı değişikliklerle güncelleştirin.  
  
     Bu şekilde, <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> nesneyi dosya değişikliği bildirimleri için izlemeyi sürdürecek şekilde yönlendirdiğinde, bellekteki metin arabelleği, oluşturduğunuz değişiklikleri ve diğer tüm bekleyen düzenlemeleri yansıtır. Diskteki dosya, sizin tarafınızdan oluşturulan en son kodu ve Kullanıcı tarafından düzenlenen kodda Kullanıcı tarafından daha önce kaydedilen değişiklikleri yansıtır.  
  
5. Parametresini ' a <xref:Microsoft.VisualStudio.Shell.Interop.IVsDocDataFileChangeControl.IgnoreFileChanges%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> ayarlayarak, nesne, dosya değişikliği bildirimleri için izlemeyi sürdürmesini bildirmek için yöntemini çağırın `fIgnore` `false` .  
  
6. Kaynak kodu denetimi (SCC) durumunda olduğu gibi dosyada birkaç değişiklik yapmayı planlıyorsanız, genel dosya değiştirme hizmetine dosya değişiklik bildirimlerini geçici olarak askıya almak için bildirmeniz gerekir.  
  
     Örneğin, dosyayı yeniden yazıp zaman damgasını değiştirirseniz, her birinin yeniden yazma ve timestample işlemleri ayrı bir dosya değişikliği olayı olarak sayımında dosya değişiklik bildirimlerini askıya almalısınız. Genel dosya değişikliği bildirimini etkinleştirmek için yöntemini çağırmanız gerekir <xref:Microsoft.VisualStudio.Shell.Interop.IVsFileChangeEx.IgnoreFile%2A> .  
  
## <a name="example"></a>Örnek  
 Aşağıda, dosya değişikliği bildiriminin nasıl bastırılacağını gösterilmektedir.  
  
```cpp#  
//Misc. helper classes  
  
CSuspendFileChanges::CSuspendFileChanges(  
    /* [in] */ const CString& strMkDocument,   
    /* [in] */ BOOL fSuspendNow /* = TRUE */)   
:  
    m_strMkDocument(strMkDocument),  
    m_fFileChangeSuspended(FALSE)  
{  
    if(fSuspendNow)  
        Suspend();  
}  
CSuspendFileChanges::~CSuspendFileChanges()  
{  
    Resume();  
}  
void CSuspendFileChanges::Suspend()  
{  
    USES_CONVERSION;  
  
    // Prevent suspend from suspending more than once.  
    if(m_fFileChangeSuspended)  
        return;  
  
    IVsRunningDocumentTable* pRDT =   
      _VxModule.GetIVsRunningDocumentTable();  
    ASSERT(pRDT);  
    if (!pRDT)  
        return;  
  
    CComPtr<IUnknown> srpDocData;  
    VSCOOKIE vscookie = VSCOOKIE_NIL;  
    pRDT->FindAndLockDocument(RDT_NoLock, T2COLE(m_strMkDocument),    
      NULL, NULL, &srpDocData, &vscookie);  
    if ( (vscookie == VSCOOKIE_NIL) || !srpDocData)  
        return;  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
    {  
        m_fFileChangeSuspended = TRUE;  
        srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, TRUE);   
        srpDocData->QueryInterface(IID_IVsDocDataFileChangeControl,   
          (void**)&m_srpIVsDocDataFileChangeControl);  
        if(m_srpIVsDocDataFileChangeControl)  
            m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(TRUE);  
    }  
}  
void CSuspendFileChanges::Resume()  
{  
    if(!m_fFileChangeSuspended)  
        return;  
  
    CComPtr<IVsFileChangeEx> srpIVsFileChangeEx;  
    HRESULT hr = _VxModule.QueryService(SID_SVsFileChangeEx,   
      IID_IVsFileChangeEx, (void **)&srpIVsFileChangeEx);  
    if (SUCCEEDED(hr) && srpIVsFileChangeEx)  
  
    srpIVsFileChangeEx->IgnoreFile(NULL, m_strMkDocument, FALSE);   
    if(m_srpIVsDocDataFileChangeControl)  
        m_srpIVsDocDataFileChangeControl->IgnoreFileChanges(FALSE);  
    m_fFileChangeSuspended = FALSE;  
    m_srpIVsDocDataFileChangeControl.Release();  
}  
// Misc. helper classes  
```  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Büyük/küçük harf, SCC durumunda olduğu gibi dosyada birden fazla değişiklik içeriyorsa, dosya değişikliklerine yönelik izlemeye geri dönmek için belge verilerini uyarmadan önce genel dosya değişiklik bildirimlerini sürdürmeniz önemlidir.
