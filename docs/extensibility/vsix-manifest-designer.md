---
title: VSıX bildirim Tasarımcısı | Microsoft Docs
description: vsıx bildirim tasarımcısı 'nın bir Visual Studio uzantısı için yükleme davranışını ayarlayan bir vsıx paketi bildirim dosyasını nasıl değiştirdiğine öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 75d11020681cb89d8e87e67abb907e84e4308348
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366806"
---
# <a name="vsix-manifest-designer"></a>VSIX Bildirim Tasarımcısı
bir Visual Studio uzantısı için yükleme davranışını ayarlayan bir vsıx paketi bildirim dosyasını değiştirir.

**VSIX bildirim Tasarımcısı** , temel alınan VSIX şemasına eşlenir. Şemadaki her öğe, tasarımcıda karşılık gelen bir denetim kullanılarak ayarlanabilir. Şema hakkında daha fazla bilgi için bkz. [VSIX uzantı şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md).

**VSIX bildirim tasarımcısını** açmak için **Çözüm Gezgini** bir *kaynak. Extension. valtmanifest* dosyası bulun ve dosyayı açın. Dosya geçerli XML içermiyorsa, bildirim Tasarımcısı açılmaz.

> [!NOTE]
> *Kaynak. Extension. valtmanifest* dosyası, paket oluşturulduğunda *. valtmanifest uzantısına* çıktıdır.

## <a name="uielement-list"></a>UIElement listesi
**VSIX bildirim Tasarımcısı** , şemanın bu üst düzey öğelerine karşılık gelen dört bölüm içerir:

- Meta veri
- Hedefleri yükler
- Varlıklar
- Bağımlılıklar

Başlık alanı aşağıdaki denetimleri içerir:

- **Ürün adı** uzantı adını tanımlar.
- **Ürün kimliği** , bu pakete ilişkin benzersiz kimlik bilgilerini belirtir.
- **Yazar** uzantının yazarının adını belirtir.
- **Sürüm** , uzantının sürüm numarasını belirtir.

**Meta veri** sekmesi aşağıdaki denetimleri içerir:

- **Açıklama** uzantı **Yöneticisi**'nde görüntülenmek üzere uzantının metin açıklamasını sağlar.
- **Dil** , bildirimde bulunan metin verilerine karşılık gelen paket için varsayılan dili belirtir. `Language`Öznitelik, kaynak derlemeler için ortak dil çalışma zamanı (CLR) yerel ayar kodu kuralını izler, örneğin, en-US, en, fr-fr. Varsayılan olarak değer tarafsız olduğundan, paketin Visual Studio herhangi bir dil sürümünde çalışacağı anlamına gelir.
- **Lisans** , varsa, Kullanıcı lisansını içeren metin dosyasını belirtir.
- **Simge** , bir simge varsa **Uzantı Yöneticisi**'nde görüntülenecek simgeyi içeren grafik dosyasını (*.png*, *.bmp*, *. jpeg*, *. ico*) belirtir. Simge resminin 32x32 piksel olması veya bu boyutlara yeniden boyutlandırılması gerekir. Hiçbir simge belirtilmemişse, **Uzantı Yöneticisi** varsayılan bir simge kullanır.
- **Önizleme resmi** , bir önizleme görüntüsü varsa, **Uzantı Yöneticisi**'nde görüntülenecek önizleme görüntüsünü içeren grafik dosyasını (*.png*, *.bmp*, *. jpeg*, *. ico*) belirtir. Önizleme resmi 200x200 piksel olmalıdır. Hiçbir önizleme görüntüsü belirtilmediyse, **Uzantı Yöneticisi** varsayılan bir görüntü kullanır.
- **Etiketler** , arama ipuçları için kullanılacak metin etiketleri ekler.
- **Sürüm notları** , sürüm notlarını içeren bir dosyayı (*.txt*, *. rtf*) belirtir. Ayrıca sürüm notlarını görüntüleyen bir Web sitesinin URL 'sini alır.
- Başlarken **Kılavuzu** , UZANTıYı veya VSIX paketindeki içeriği kullanma hakkında bilgi içeren bir dosyayı (*.txt*, *. rtf*) belirtir. Bu kılavuz, uzantı yüklemesi tamamlandığında görüntülenir. Ayrıca, kılavuzunu görüntüleyen bir Web sitesinin URL 'sini de alır.
- **Daha fazla bilgi URL 'si** , ürünle ilgili ek bilgiler içeren bir Web sitesinin URL 'sini belirtir.

**Hedefleri yükler** sekmesi aşağıdaki denetimleri içerir:

- hedef yükleme türleri olarak **uzantı** ve **uzantı SDK** Visual Studio **yükleme listelerinin türü** . Seçenekler, seçtiğiniz türe göre farklılık gösterir.
  - **Visual Studio uzantısı** , paketin nasıl yüklenebileceğini ve bu uzantının hangi Visual Studio ürünlerine yüklenebileceğini açıklayan **ınstalyüklemi hedef** öğelerini listeler. Her ürün, ad ve sürüm veya sürüm aralığıyla ayrı olarak tanımlanır. Ürünler listeye eklenebilir, değiştirilebilir ve silinebilir. Bir ürünün adı ve sürümü, ilişkili **ınstaltarget** öğesinin **kimlik** ve **Sürüm** özniteliklerine karşılık gelir.
    - **Sürüm aralığı** [12,0, 14,0] ve aşağıdaki gösterimi kullanır:
      - `[` -En düşük sürüm dahil
      - `]` -en yüksek sürüm dahil
      - `(` -En düşük sürüm dışlamalı
      - `)` -en yüksek sürüm dışlamalı
      - Tek sürüm #-yalnızca belirtilen sürüm

  - **Uzantı SDK 'sı** , belirli bir ürün ve sürüm kapsamındaki genel yüklemeyi belirtir. **hedef platform tanımlayıcısı** , hedeflediğiniz "Windows," gibi bir platformdur. **Hedef platform sürümü** , hedef platformunuzun 8,0 gibi sürümüdür. SDK **adı** ve **SDK sürümü** , SDK 'nın sırasıyla adı ve sürüm numarasıdır.

- **Bu VSIX tüm kullanıcılar için yüklendi (yükleme sırasında yükseltme gerektirir)**. Bu onay kutusunu seçerseniz, uzantı tüm kullanıcılar için yüklenir; Aksi takdirde, yalnızca geçerli kullanıcı için yüklenir.

- **bu vsıx Windows Installer tarafından yüklendi**. bu onay kutusunu seçerseniz, uzantı Windows Installer (*.msi* dosyası) tarafından yüklenir; aksi takdirde, tipik bir vsıx paketi (*. VSIX* dosyası) olarak yüklenir.

**Varlıklar** sekmesi aşağıdaki denetimleri içerir:

- Varlık **listesi** , bu paketin yüzeylerinin uzantısını veya içerik öğelerini tanımlayan varlık öğelerini listeler. Her uzantı veya içerik öğesi, kaynak, tür ve yol tarafından ayrı olarak listelenir. Uzantılar ve içerik öğeleri listeye eklenebilir, değiştirilebilir ve silinebilir. Uzantı veya içerik öğesinin türü ve yolu `Type` `Path` ilişkili öğenin ve özniteliklerine karşılık gelir `Asset` . Aşağıdaki türler bilinmektedir:
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

**Bağımlılıklar** sekmesi aşağıdaki denetimleri içerir:

- **Ad, kaynak ve sürüm aralığı** , bu paketin bağımlı olduğu diğer paketler olan bu paketin bağımlılık öğelerini listeler. Bir bağımlılık paketi belirtilmişse, bu paket yüklenmeden önce yüklenmesi gerekir; Aksi takdirde, bu paketin yüklemesi gerekir.

   Bağımlılık paketleri tanımlayıcı, ad, sürüm aralığı, kaynak ve bağımlılığın nasıl çözümleneceği ile belirtilir. Her bağımlılık paketi, ad, sürüm ve kaynak tarafından ayrı olarak listelenir. Bağımlılık paketleri listeye eklenebilir, değiştirilebilir ve silinebilir.

   Tanımlayıcının, `ID` bağımlılık paketi meta verilerinin özniteliğiyle eşleşmesi gerekir. Kaynak, geçerli çözümdeki bir proje, şu anda yüklü bir uzantı veya bir dosya olabilir. **Bağımlılık çözümlenmiş** ayarı, iç içe geçmiş bir paketin göreli yolu veya bağımlılık için karşıdan yükleme konumunun URL 'si olabilir. Bağımlılık paketinin KIMLIĞI, sürümü ve çözümü `Id` , `Version` ilişkili öğenin, ve özniteliklerine karşılık gelir `Location` `Dependency` .

## <a name="see-also"></a>Ayrıca bkz.
- [VSıX uzantı Şeması 2,0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSıX paketinin anatomumu](../extensibility/anatomy-of-a-vsix-package.md)
