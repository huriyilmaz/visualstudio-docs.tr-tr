---
title: Akıllı ana bilgisayar yardımcı arabirimlerini uygulama | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Smart Host Helper Interfaces, implementing
ms.assetid: b9c44246-4d4d-469e-91be-00c8f5796fa5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9b387999d71690deaf5bea30a07439677065d63d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574380"
---
# <a name="implementing-smart-host-helper-interfaces"></a>Akıllı Konak Yardımcı Arabirimleri Uygulama
[Idebugbelge\arabirim](../winscript/reference/idebugdocumenthelper-interface.md) arabirimi, akıllı barındırma için gereken birçok arabirime yönelik uygulamalar sağladığından, etkin hata ayıklama için akıllı ana bilgisayar oluşturma görevini büyük ölçüde basitleştirir.  
  
 @No__t_0 kullanarak bir akıllı ana bilgisayar olması için, bir ana bilgisayar uygulamasının yalnızca üç şey yapması gerekir:  
  
1. Işlem hata ayıklama yöneticisini `CoCreate` ve uygulamanızı hata ayıklanabilir uygulamalar listesine eklemek için [ıprocessdebugmanager arabirimi](../winscript/reference/iprocessdebugmanager-interface.md) arabirimini kullanın.  
  
2. [Iprocessdebugmanager:: Createdebugbelgethelper](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md) metodunu kullanarak her betik nesnesi için bir hata ayıklama belgesi Yardımcısı oluşturun. Belge adı, üst belge, metin ve betik bloklarının tanımlandığından emin olun.  
  
3. [Iactivescriptsitedebug Interface](../winscript/reference/iactivescriptsitedebug-interface.md) arabirimini, [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) arabirimini (etkin komut dosyası için gereklidir) uygulayan nesneniz üzerinde uygulayın. @No__t_0 arabirimindeki basit olmayan tek yöntem, yardımcıya temsilci atamak için yeterlidir.  
  
   İsteğe bağlı olarak, ana bilgisayar, sözdizimi rengi, belge bağlamı oluşturma ve diğer genişletilmiş işlevler üzerinde ek denetime ihtiyaç duyuyorsa [ıdebugbelgesiyle Thost arabirimi](../winscript/reference/idebugdocumenthost-interface.md) arabirimini uygulayabilir.  
  
   Akıllı ana bilgisayar Yardımcısı üzerindeki ana sınırlama, yalnızca içeriği eklendikten sonra değişiklik veya küçültme sonrasında (belgeler genişlebilse de) yalnızca içeriğini işleyebilmelerdir. Ancak birçok akıllı ana bilgisayar için, sağladığı işlevsellik tam olarak gerekli değildir.  
  
   Aşağıdaki bölümlerde her bir adım daha ayrıntılı açıklanmaktadır.  
  
## <a name="create-an-application-object"></a>Uygulama nesnesi oluşturma  
 Akıllı ana bilgisayar Yardımcısı kullanılmadan önce, hata ayıklayıcıda uygulamanızı temsil etmek için bir [IDebugApplication Interface](../winscript/reference/idebugapplication-interface.md) nesnesi oluşturulması gerekir.  
  
#### <a name="to-create-an-application-object"></a>Uygulama nesnesi oluşturmak için  
  
1. @No__t_0 kullanarak işlem hata ayıklama Yöneticisi 'nin bir örneğini oluşturun.  
  
2. [Iprocessdebugmanager:: CreateApplication](../winscript/reference/iprocessdebugmanager-createapplication.md)öğesini çağırın.  
  
3. [IDebugApplication:: SetName](../winscript/reference/idebugapplication-setname.md)kullanarak uygulamada adı ayarlayın.  
  
4. [Iprocessdebugmanager:: Addadpplication](../winscript/reference/iprocessdebugmanager-addapplication.md)kullanarak uygulama nesnesini hata ayıklanabilir uygulamalar listesine ekleyin.  
  
     Aşağıdaki kod süreci özetler, ancak hata denetimini veya diğer güçlü programlama tekniklerini içermez.  
  
    ```cpp
    CoCreateInstance(CLSID_ProcessDebugManager, NULL,  
          CLSCTX_INPROC_SERVER | CLSCTX_INPROC_HANDLER  
          | CLSCTX_LOCAL_SERVER,  
    IID_IProcessDebugManager, (void **)&g_ppdm);  
    g_ppdm->CreateApplication(&g_pda);  
    g_pda->SetName(L"My cool application");  
    g_ppdm->AddApplication(g_pda, &g_dwAppCookie);  
    ```  
  
## <a name="using-idebugdocumenthelper"></a>Idebugbelgethelper 'ı kullanma  
  
#### <a name="to-use-the-helper-minimal-sequence-of-steps"></a>Yardımcıyı kullanmak için (en az adım dizisi)  
  
1. Her ana bilgisayar belgesi için [ıprocessdebugmanager:: Createdebugbelgeadı](../winscript/reference/iprocessdebugmanager-createdebugdocumenthelper.md)' nı kullanarak bir yardımcı oluşturun.  
  
2. Yardımcı üzerinde [ıdebugbelgesiyle thelper:: Init](../winscript/reference/idebugdocumenthelper-init.md) çağırın, bu adı, belge özniteliklerini ve benzerlerini yapın.  
  
3. Belgenin ağaç içinde konumunu tanımlamak ve hata ayıklayıcıya görünür hale getirmek için [ıdebugbelgethelper::](../winscript/reference/idebugdocumenthelper-attach.md) belge için üst yardımcı ile (veya belge kök ise null) Attach ' i çağırın.  
  
4. Belgenin metnini tanımlamak için [ıdebugbelgethelper:: AddDBCSText](../winscript/reference/idebugdocumenthelper-adddbcstext.md) veya [ıdebugbelgesiyle Thelper:: addunicodetext](../winscript/reference/idebugdocumenthelper-addunicodetext.md) öğesini çağırın. (Tarayıcı söz konusu olduğunda olduğu gibi, belge artımlı olarak indirildiyse bunlar birden çok kez çağrılabilir.)  
  
5. Her bir betik bloğu ve ilişkili betik altyapısı için aralıkları tanımlamak üzere [ıdebugbelgethelper::D efineScriptBlock](../winscript/reference/idebugdocumenthelper-definescriptblock.md) ' i çağırın.  
  
## <a name="implementing-iactivescriptsitedebug"></a>Iactivescriptsitedebug uygulama  
 [Iactivescriptsitedebug:: GetDocumentContextFromPosition](../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)uygulamak için, belirtilen siteye karşılık gelen yardımcıyı alın ve ardından belirtilen kaynak bağlamı için başlangıç belgesi sapmasını aşağıdaki gibi alın:  
  
```cpp
pddh->GetScriptBlockInfo(dwSourceContext, NULL, &ulStartPos, NULL);  
```  
  
 Ardından, verilen karakter boşluğu için yeni bir belge bağlamı oluşturmak için yardımcı 'yı kullanın:  
  
```cpp
pddh->CreateDebugDocumentContext(ulStartPos + uCharacterOffset, cChars, &pddcNew);  
```  
  
 [Iactivescriptsitedebug:: GetRootApplicationNode](../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)öğesini uygulamak için yalnızca `IDebugApplication::GetRootNode` ( [IRemoteDebugApplication:: GetRootNode](../winscript/reference/iremotedebugapplication-getrootnode.md)öğesinden devralınmış) öğesini çağırın.  
  
 [Idebugbelgethelper:: GetDebugApplicationNode](../winscript/reference/idebugdocumenthelper-getdebugapplicationnode.md)uygulamak için, işlem hata ayıklama Yöneticisi ' ni kullanarak başlangıçta oluşturduğunuz `IDebugApplication` döndürün.  
  
## <a name="the-optional-idebugdocumenthost-interface"></a>İsteğe bağlı ıdebugbelgethost arabirimi  
 Ana bilgisayar, yardımcı üzerinde ek denetim sağlamak için [ıdebugbelgethelper:: Setdebugbelgethost](../winscript/reference/idebugdocumenthelper-setdebugdocumenthost.md) ' nı kullanarak [ıdebugbelgethost arabiriminin](../winscript/reference/idebugdocumenthost-interface.md) bir uygulamasını sağlayabilir. Konak arabiriminin şunları yapmasına izin verdiği bazı önemli noktalar şunlardır:  
  
- Ana bilgisayarın gerçek karakterleri hemen sağlaması gerekmiyorsa [ıdebugbelgethelper:: AddDeferredText](../winscript/reference/idebugdocumenthelper-adddeferredtext.md) kullanarak metin ekleyin. Karakterler gerçekten gerektiğinde, yardımcı, konakta [ıdebugbelgethost:: GetDeferredText](../winscript/reference/idebugdocumenthost-getdeferredtext.md) öğesini çağırır.  
  
- Yardımcı tarafından sunulan varsayılan sözdizimi renklendirmesini geçersiz kılın. Yardımcı, bir karakter aralığının renklendirmesini anlamak için [ıdebugbelgethost:: GetScriptTextAttributes](../winscript/reference/idebugdocumenthost-getscripttextattributes.md) çağırır, ana bilgisayar `E_NOTIMPL` döndürmesi durumunda varsayılan uygulamasına geri döner.  
  
- [Idebugdocumentthost:: OnCreateDocumentContext](../winscript/reference/idebugdocumenthost-oncreatedocumentcontext.md)uygulayarak yardımcı tarafından oluşturulan belge bağlamları için bilinmeyen bir denetim sağlayın. Bu, konağın varsayılan belge bağlamı uygulamasının işlevselliğini geçersiz kılmasına izin verir.  
  
- Belge için dosya sisteminde bir yol adı girin. Bazı hata ayıklama Işlemi, kullanıcının belgedeki değişiklikleri düzenlemesine ve kaydetmesine izin vermek için bunu kullanır. Bir belge kaydedildikten sonra konağa bildirimde bulunan [ıdebugbelgethost:: NotifyChanged](../winscript/reference/idebugdocumenthost-notifychanged.md) çağrıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklamaya Genel Bakış](../winscript/active-script-debugging-overview.md)