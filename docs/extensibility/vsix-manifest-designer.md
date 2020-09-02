---
title: VSıX bildirim Tasarımcısı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80697889"
---
# <a name="vsix-manifest-designer"></a>VSIX Bildirim Tasarımcısı
Bir Visual Studio uzantısı için yükleme davranışını ayarlayan bir VSıX paketi bildirim dosyasını değiştirir.

 **VSIX bildirim Tasarımcısı** , temel alınan VSIX şemasına eşlenir. Şemadaki her öğe, tasarımcıda karşılık gelen bir denetim kullanılarak ayarlanabilir. Şema hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md).

 **VSIX bildirim tasarımcısını**açmak için **Çözüm Gezgini**bir *kaynak. Extension. valtmanifest* dosyası bulun ve dosyayı açın. Dosya geçerli XML içermiyorsa, bildirim Tasarımcısı açılmaz.

> [!NOTE]
> *Kaynak. Extension. valtmanifest* dosyası, paket oluşturulduğunda *. valtmanifest uzantısına* çıktıdır.

## <a name="uielement-list"></a>UIElement listesi
 **VSIX bildirim Tasarımcısı** , şemanın bu üst düzey öğelerine karşılık gelen dört bölüm içerir:

- Meta Veriler

- Hedefleri yükler

- Varlıklar

- Bağımlılıklar

  Başlık alanı aşağıdaki denetimleri içerir.

  **Ürün adı** Uzantı adını açıklar.

  **Ürün kimliği** Bu paket için benzersiz kimlik bilgilerini belirtir.

  **Yazar** Uzantının yazarının adını belirtir.

  **Sürümü** Uzantının sürüm numarasını belirtir.

  **Meta veri** sekmesi aşağıdaki denetimleri içerir.

  **Açıklama** Uzantı **Yöneticisi**'nde görüntülenmek üzere uzantının metin açıklamasını sağlar.

  **Dil** Bildirimde bulunan metin verilerine karşılık gelen paket için varsayılan dili belirtir. `Language`Öznitelik, kaynak derlemeler için ortak dil çalışma zamanı (CLR) yerel ayar kodu kuralını izler, örneğin, en-US, en, fr-fr. Varsayılan olarak değer tarafsız olduğundan, paketin Visual Studio 'nun herhangi bir dil sürümünde çalışacağı anlamına gelir.

  **Lisans** Varsa, Kullanıcı lisansını içeren metin dosyasını belirtir.

  **Simge** Bir simge varsa **Uzantı Yöneticisi**'nde görüntülenecek simgeyi içeren grafik dosyasını (*. png*, *. bmp*, *. jpeg*, *. ico*) belirtir. Simge resminin 32x32 piksel olması veya bu boyutlara yeniden boyutlandırılması gerekir. Hiçbir simge belirtilmemişse, **Uzantı Yöneticisi** varsayılan bir simge kullanır.

  **Önizleme resmi** Bir önizleme görüntüsü varsa, **Uzantı Yöneticisi**'nde görüntülenecek önizleme görüntüsünü içeren grafik dosyasını (*. png*, *. bmp*, *. jpeg*, *. ico*) belirtir. Önizleme resmi 200x200 piksel olmalıdır. Hiçbir önizleme görüntüsü belirtilmediyse, **Uzantı Yöneticisi** varsayılan bir görüntü kullanır.

  **Etiketler** Arama ipuçları için kullanılacak metin etiketleri ekler.

  **Sürüm notları** Sürüm notlarını içeren bir dosyayı (*. txt*, *. rtf*) belirtir. Ayrıca sürüm notlarını görüntüleyen bir Web sitesinin URL 'sini alır.

  **Başlarken Kılavuzu** Uzantıyı veya VSıX paketindeki içeriği kullanma hakkında bilgi içeren bir dosyayı (*. txt*, *. rtf*) belirtir. Bu kılavuz, uzantı yüklemesi tamamlandığında görüntülenir. Ayrıca, kılavuzunu görüntüleyen bir Web sitesinin URL 'sini de alır.

  **Daha fazla bilgi URL 'si** Ürünle ilgili ek bilgi içeren bir Web sitesinin URL 'sini belirtir.

  **Hedefleri yükler** sekmesi aşağıdaki denetimleri içerir.

  **Yüklemenin türü** **Visual Studio uzantısı** ve **Uzantı SDK 'sını** hedef yükleme türleri olarak listeler. Seçenekler, seçtiğiniz türe göre farklılık gösterir.

  **Visual Studio uzantısı** Paketin nasıl yüklenebileceğini ve bu uzantının hangi Visual Studio ürünlerine yüklenebileceğini açıklayan **ınstalyüklemi hedef** öğelerini listeler. Her ürün, ad ve sürüm veya sürüm aralığıyla ayrı olarak tanımlanır. Ürünler listeye eklenebilir, değiştirilebilir ve silinebilir. Bir ürünün adı ve sürümü, ilişkili **ınstaltarget** öğesinin **kimlik** ve **Sürüm** özniteliklerine karşılık gelir.

  **Sürüm aralığı** [12,0, 14,0] ve aşağıdaki gösterimi kullanır:

- [-en düşük sürüm dahil

- ]-en yüksek sürüm dahil

- (-en düşük sürüm dışlamalı

- )-en yüksek sürüm dışlamalı

- Tek sürüm #-yalnızca belirtilen sürüm

  **Uzantı SDK 'sı** Belirli bir ürün ve sürüm kapsamındaki genel yüklemeyi belirtir. **Hedef platform tanımlayıcısı** , hedeflediğiniz "Windows" gibi bir platformdur. **Hedef platform sürümü** , hedef platformunuzun 8,0 gibi sürümüdür. SDK **adı** ve **SDK sürümü** , SDK 'nın sırasıyla adı ve sürüm numarasıdır.

  **Bu VSIX tüm kullanıcılar için yüklendi (yükleme sırasında yükseltme gerektirir)** Bu onay kutusunu seçerseniz, uzantı tüm kullanıcılar için yüklenir; Aksi takdirde, yalnızca geçerli kullanıcı için yüklenir.

  **Bu vsıx Windows Installer tarafından yüklendi** Bu onay kutusunu seçerseniz, uzantı Windows Installer (*. msi* dosyası) tarafından yüklenir; Aksi halde, tipik bir VSıX paketi (*. VSIX* dosyası) olarak yüklenir.

  **Varlıklar** sekmesi aşağıdaki denetimleri içerir.

  **Varlıkların listesi** Bu paketin yüzeylerinin uzantısını veya içerik öğelerini tanımlayan varlık öğelerini listeler. Her uzantı veya içerik öğesi, kaynak, tür ve yol tarafından ayrı olarak listelenir. Uzantılar ve içerik öğeleri listeye eklenebilir, değiştirilebilir ve silinebilir. Uzantı veya içerik öğesinin türü ve yolu `Type` `Path` ilişkili öğenin ve özniteliklerine karşılık gelir `Asset` . Aşağıdaki türler bilinmektedir:

- Microsoft. VisualStudio. Package

- Microsoft. VisualStudio. MefComponent

- Microsoft. VisualStudio. ToolboxControl

- Microsoft. VisualStudio. Samples

- Microsoft. VisualStudio. ProjectTemplate

- Microsoft. VisualStudio. ItemTemplate

- Microsoft. VisualStudio. Assembly

- Microsoft. ExtensionSDK

  Bir varlık eklemek veya düzenlemek için varlık türünü, varlığın geçerli çözümde bir proje mi yoksa dosya sistemindeki bir dosya ve projenin adını da belirtmeniz gerekir. Ayrıca, içine katıştırılacak klasörün adını da belirtebilirsiniz.

  Ayrıca kendi türlerinizi oluşturabilir ve bunlara benzersiz adlar verebilirsiniz.

  **Bağımlılıklar** sekmesi aşağıdaki denetimleri içerir.

  **Ad, kaynak ve sürüm aralığı** Bu paketin bağımlı olduğu diğer paketler olan bu paketin bağımlılık öğelerini listeler. Bir bağımlılık paketi belirtilmişse, bu paket yüklenmeden önce yüklenmesi gerekir; Aksi takdirde, bu paketin yüklemesi gerekir.

  Bağımlılık paketleri tanımlayıcı, ad, sürüm aralığı, kaynak ve bağımlılığın nasıl çözümleneceği ile belirtilir. Her bağımlılık paketi, ad, sürüm ve kaynak tarafından ayrı olarak listelenir. Bağımlılık paketleri listeye eklenebilir, değiştirilebilir ve silinebilir.

  Tanımlayıcının, `ID` bağımlılık paketi meta verilerinin özniteliğiyle eşleşmesi gerekir. Kaynak, geçerli çözümdeki bir proje, şu anda yüklü bir uzantı veya bir dosya olabilir. **Bağımlılık çözümlenmiş** ayarı, iç içe geçmiş bir paketin göreli yolu veya bağımlılık için karşıdan yükleme konumunun URL 'si olabilir. Bağımlılık paketinin KIMLIĞI, sürümü ve çözümü `Id` , `Version` ilişkili öğenin, ve özniteliklerine karşılık gelir `Location` `Dependency` .

## <a name="see-also"></a>Ayrıca bkz.
- [VSıX uzantı Şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)
