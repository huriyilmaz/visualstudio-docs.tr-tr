---
title: Eski Dil Hizmeti1 hizmetlerinde parametre | Microsoft Docs
description: Eski dil hizmetlerinde kullanıcılara ipuçları sağlayan IntelliSense Parametre Bilgisi araç ipucunu nasıl uygulayacağız?
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b8c3a0cdec47be7ce5d29ff5b43ac6cd7e05cc07
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049785"
---
# <a name="parameter-info-in-a-legacy-language-service-1"></a>Eski dil hizmetlerinde Parametre Bilgileri 1
IntelliSense Parametre Bilgisi araç ipucu, kullanıcılara dil yapısında nerede olduklarının ipuçlarını sağlar.

 Eski dil hizmetleri VSPackage'ın bir parçası olarak uygulanır, ancak dil hizmeti özelliklerini uygulamanın daha yeni yolu MEF uzantılarını kullanmaktır. Daha fazla bilgi için [bkz. Düzenleyiciyi ve Dil Hizmetlerini Genişletme.](../../extensibility/extending-the-editor-and-language-services.md)

> [!NOTE]
> Yeni düzenleyici API'sini mümkün olan en kısa sürede kullanmaya başlamayı öneririz. Bu, dil hizmetinizin performansını artırır ve yeni düzenleyici özelliklerinden yararlanmanızı sağlar.

## <a name="how-parameter-info-tooltips-work"></a>Parametre Bilgisi Araç İpucu Nasıl Çalışır?
 Düzenleyicide bir deyimini yazarak VSPackage, yazılmış olan deyimin tanımını içeren küçük bir araç ipucu penceresi görüntüler. Örneğin, bir Microsoft Foundation Sınıfları (MFC) deyimi (örneğin) yazın ve parametreleri listelemeye başlamak için açma parantez tuşuna basın, yöntemin tanımını görüntüleyen bir yöntem ipucu `pMainFrame ->UpdateWindow` `UpdateWindow` görüntülenir.

 Parametre Bilgisi araç ipucu genellikle deyim tamamlama ile birlikte kullanılır. Bunlar, yöntem adı veya anahtar sözcüğünün ardından parametreleri veya diğer biçimlendirilmiş bilgileri olan diller için kullanışlıdır.

 Parametre Bilgisi araç ipucu, komut kesme yoluyla dil hizmeti tarafından başlatılır. Kullanıcı karakterlerine müdahale etmek için dil hizmeti nesnenizin arabirimini uygulaması ve arabiriminde yöntemini çağırarak uygulamanıza yönelik bir metin görünümü <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> işaretçisi geçmesi <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> gerekir. Komut filtresi, kod penceresine yazarak komutlara müdahale ediyor. Kullanıcıya parametre bilgilerini ne zaman gösterebilirsiniz? için komut bilgilerini izleme. Deyim tamamlama, hata işaretçileri vb. için aynı komut filtresini kullanabilirsiniz.

 Dil hizmetinin ipuçları sağlaya bir anahtar sözcük yazmanız, dil hizmeti bir nesnesi oluşturur ve IDE'ye ipucunu görüntülemesi için bunu bildirmek için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> arabiriminde yöntemini arar. kullanarak <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> ve `VSLocalCreateInstance` coclass belirterek nesnesini `CLSID_VsMethodTipWindow` oluşturun. `VsLocalCreateInstance` , yerel kayıt defteri için çağıran ve için bu nesnede çağıran vsdoc.h `QueryService` üst bilgi dosyasında tanımlanan bir `CreateInstance` `CLSID_VsMethodTipWindow` işlevdir.

## <a name="providing-a-method-tip"></a>Yöntem İpucu Sağlama
 Yöntem ipucu sağlamak için <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> arabiriminde yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> çağırarak arabiriminizin uygulamasını <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> geçirmeniz gerekir.

 Sınıfınız <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> çağrıldığında, yöntemleri aşağıdaki sırayla çağrılır:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Geçerli metin arabelleğinde ilgili verilerin konumunu ve uzunluğunu döndürür. Bu, IDE'ye bu verileri araç ipucu penceresiyle karartmama talimatı sağlar.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Başlangıçta görüntülenebilir istediğiniz yöntem numarasını (sıfır tabanlı dizin) döndürür. Örneğin, sıfırı iade ediyorsanız, ilk aşırı yüklenmiş yöntem başlangıçta sunulmuştur.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Geçerli bağlamda geçerli olan aşırı yüklenmiş yöntemlerin sayısını döndürür. Bu yöntem için 1'den büyük bir değer dönerse metin görünümü sizin için yukarı ve aşağı okları görüntüler. Aşağı oka tıklarsanız IDE yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> arar. Yukarı oka tıklarsanız IDE yöntemini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> arar.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Parametre Bilgisi araç ipucu metni, ve yöntemlerine yapılan birkaç çağrı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> sırasında <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> oluşturulur.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     yönteminde görüntülemek için parametre sayısını döndürür.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Görüntülenebilir istediğiniz aşırı yüke karşılık gelen bir yöntem numarası iade ediyorsanız, bu yöntem çağrılır ve ardından yöntemine yapılan bir <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> çağrı ile birlikte bu yöntem çağrılır.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Yöntem ipucu görüntülendiğinde dil hizmetinizi düzenleyiciyi güncelleştirmesi için bilgi sağlar. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>yönteminde, aşağıdaki çağrıyı yapın:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Yöntem ipucu penceresini <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> kapatarak yöntemine bir çağrı alırsınız.
