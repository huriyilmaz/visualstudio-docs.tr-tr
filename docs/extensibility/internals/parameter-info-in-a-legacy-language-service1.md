---
title: Eski Dil Hizmetinde Parametre Bilgisi1 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706797"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Eski Dil Hizmetinde Parametre Bilgileri
IntelliSense Parametre Bilgi araç ipucu, kullanıcılara bir dil yapısında nerede oldukları hakkında ipuçları sağlar.

 Eski dil hizmetleri BIR VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın en yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [Editör ve Dil Hizmetlerini Genişletme'ye](../../extensibility/extending-the-editor-and-language-services.md)bakın.

> [!NOTE]
> Yeni düzenleyici API'yi mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="how-parameter-info-tooltips-work"></a>Parametre Bilgi Araç İpuçları Nasıl Çalışır?
 Düzenleyiciye bir deyim yazdığınızda, VSPackage yazılan deyimin tanımını içeren küçük bir araç ucu penceresi görüntüler. Örneğin, bir Microsoft Hazırlık Sınıfları (MFC) deyimi `pMainFrame ->UpdateWindow`(örneğin) yazarsanız ve liste parametrelerini başlatmak için açılış parantez anahtarına `UpdateWindow` basarsanız, yöntemin tanımını gösteren bir yöntem ipucu görüntülenir.

 Parametre Bilgi araç ipuçları genellikle deyimi tamamlama ile birlikte kullanılır. Bunlar en çok yöntem adı veya anahtar kelimeden sonra parametreleri veya diğer biçimlendirilmiş bilgilere sahip diller için yararlıdır.

 Parametre Bilgisi araç ipuçları, dil hizmeti tarafından komut engelleme yoluyla başlatılır. Kullanıcı karakterlerini engellemek için, dil hizmeti <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> nesneniz arabirimi uygulamalı ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabirimdeki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> yöntemi çağırarak uygulamanız için bir işaretçi metin görünümü geçirmelidir. Komut filtresi, kod penceresine yazdığınız komutları keser. Parametre bilgilerini kullanıcıya ne zaman gösterin gerektiğini bilmek için komut bilgilerini izleyin. Ekstre tamamlama, hata işaretçileri vb. için aynı komut filtresini kullanabilirsiniz.

 Dil hizmetinin ipuçları sağlayabileceği bir anahtar kelime yazdığınızda, dil hizmeti <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> bir nesne <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> oluşturur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> ve bir ipucu görüntülemek için IDE'yi bildirmek için arabirimdeki yöntemi çağırır. Nesneyi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> kullanarak `VSLocalCreateInstance` ve birlikte sınıfı `CLSID_VsMethodTipWindow`belirterek oluşturun. `VsLocalCreateInstance`üstbilgi vdoc.h'de tanımlanan ve yerel `QueryService` kayıt defterini çağıran `CreateInstance` ve bu `CLSID_VsMethodTipWindow`nesneyi .

## <a name="providing-a-method-tip"></a>Yöntem İpucu Sağlama
 Bir yöntem ipucu sağlamak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> için, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> arabirimdeki yöntemi çağırın ve arabirimin uygulanmasını geçirin.

 Sınıfınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> çağrıldığında, yöntemleri aşağıdaki sırada çağrılır:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Geçerli metin arabelleğindeki ilgili verilerin konumunu ve uzunluğunu verir. Bu, IDE'ye araç ucu penceresiyle bu verileri gizlememesi talimatını verir.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Başlangıçta görüntülenmesini istediğiniz yöntem numarasını (sıfır tabanlı dizin) döndürür. Örneğin, sıfır döndürerseniz, ilk aşırı yüklenen yöntem başlangıçta sunulur.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Geçerli bağlamda geçerli olan aşırı yüklenen yöntem sayısını verir. Bu yöntem için 1'den büyük bir değer döndürerseniz, metin görünümü sizin için yukarı ve aşağı okları görüntüler. Aşağı ok'u tıklattığınızda, IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> yöntemi çağırır. Yukarı ok'u tıklattığınızda, IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> yöntemi çağırır.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Parametre Bilgi araç ucunun metni, çeşitli aramalar <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> sırasında ve yöntemlerde oluşturulur.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Yöntemde görüntülenecek parametre sayısını döndürür.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Görüntülenmesini istediğiniz aşırı yüklemeyle karşılık gelen bir yöntem numarası döndürerseniz, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> bu yöntem çağrılır ve ardından yönteme çağrı yapılır.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Bir yöntem ipucu görüntülendiğinde düzenleyiciyi güncelleştirmesi için dil hizmetinizi bilgilendirir. Yöntemde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> aşağıdakileri arayın:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Yöntem ipucu penceresini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> kapattığınızda yönteme bir çağrı alırsınız.
