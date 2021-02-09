---
title: Eski dilde parametre bilgisi Service1 | Microsoft Docs
description: Kullanıcılara eski bir dil hizmetinde ipuçları sağlayan IntelliSense parametre bilgisi araç ipucunu nasıl uygulayacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d43737467ca063cfcfa6ef99cb8df5a31395c3ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895451"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Eski dil hizmeti 1 ' de parametre bilgisi
IntelliSense parametre bilgisi araç ipucu kullanıcılara bir dil yapısında oldukları yerleri hakkında ipuçları sağlar.

 Eski dil Hizmetleri VSPackage 'un bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamak için daha yeni bir yol MEF uzantıları kullanmaktır. Daha fazla bilgi edinmek için bkz. [düzenleyiciyi ve dil hizmetlerini genişletme](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Yeni Düzenleyici API 'sini mümkün olan en kısa sürede kullanmaya başlamanızı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="how-parameter-info-tooltips-work"></a>Parametre bilgileri araç Ipuçları nasıl çalışır?
 Düzenleyicide bir ifade yazdığınızda, VSPackage, yazılan deyimin tanımını içeren küçük bir araç ipucu penceresi görüntüler. Örneğin, (gibi) bir Microsoft Foundation Sınıfları (MFC) ifadesi yazarsanız `pMainFrame ->UpdateWindow` ve parametreleri listelemeyi başlatmak için açma ayracı tuşuna basarsanız, yöntemin tanımını görüntüleyen bir yöntem ipucu görünür `UpdateWindow` .

 Parametre bilgisi araç ipuçları genellikle deyimin tamamlanmasına birlikte kullanılır. Bunlar, yöntem adı veya anahtar sözcüğünden sonra parametreleri veya diğer biçimlendirilen bilgileri içeren diller için en yararlıdır.

 Bilgi araç ipuçları, komut yakalamasının üzerinden dil hizmeti tarafından başlatılır. Kullanıcı karakterleri için, dil hizmeti nesneniz <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimi uygulamalıdır ve <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> arabirimde yöntemi çağırarak metin görünümünü uygulamanıza bir işaretçi olarak iletmelidir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Komut filtresi, kod penceresine yazdığınız komutları karşılar. Kullanıcıya parametre bilgilerinin ne zaman görüntüleneceğini bildirmek için komut bilgilerini izleyin. Deyimde tamamlama, hata işaretçileri vb. için aynı komut filtresini kullanabilirsiniz.

 Dil hizmetinin ipuçları sağlayabileceği bir anahtar sözcük yazdığınızda, dil hizmeti bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> nesne oluşturur ve <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> IDE 'yi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> bir ipucu göstermesini bildirmek için arabirimindeki yöntemi çağırır. Öğesini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> kullanarak `VSLocalCreateInstance` ve coclass 'ı belirterek nesnesi oluşturun `CLSID_VsMethodTipWindow` . `VsLocalCreateInstance``QueryService`, yerel kayıt defteri ve `CreateInstance` için bu nesnedeki çağrıları çağıran vsdoc. h üstbilgi dosyasında tanımlanan bir işlevdir `CLSID_VsMethodTipWindow` .

## <a name="providing-a-method-tip"></a>Yöntem Ipucu sağlama
 Bir yöntem ipucu sağlamak için, arabirimindeki <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> yöntemi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> arabirimi uygulamanıza geçirerek arayüzde çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> .

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>Sınıfınız çağrıldığında, yöntemleri aşağıdaki sırada çağrılır:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Geçerli metin arabelleğindeki ilgili verilerin konumunu ve uzunluğunu döndürür. Bu, IDE 'ye araç ipucu penceresiyle verileri gizlememesini sağlar.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Başlangıçta görüntülenmesini istediğiniz yöntem numarasını (sıfır tabanlı dizin) döndürür. Örneğin, sıfır döndürtakdirde ilk aşırı yüklenmiş yöntem başlangıçta sunulur.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Geçerli bağlamda geçerli olan aşırı yüklenmiş yöntemlerin sayısını döndürür. Bu yöntem için 1 ' den büyük bir değer döndürürler, metin görünümü sizin için yukarı ve aşağı okları görüntüler. Aşağı oka tıklarsanız IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> yöntemini çağırır. Yukarı oka tıklarsanız IDE <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> yöntemini çağırır.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Parametre bilgisi araç ipucunun metni, ve yöntemlerine yapılan birkaç çağrı sırasında oluşturulur <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Yönteminde görüntülenecek parametre sayısını döndürür.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Görüntülenmesini istediğiniz aşırı yüklemeye karşılık gelen bir yöntem numarası döndürürler, bu yöntem çağrılır ve ardından yöntemine bir çağrı gelir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> .

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Dil hizmetinize, bir yöntem İpucu görüntülendiğinde düzenleyiciyi güncelleştirme hakkında bilgi verir. Yönteminde, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> aşağıdakileri çağırın:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Yöntem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> İpucu penceresini kapattığınızda yöntemine bir çağrı alırsınız.
