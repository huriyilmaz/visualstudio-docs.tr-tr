---
title: VSIX Bildirim Tasarımcısı | Microsoft Docs
description: VSIX Bildirim Tasarımcısı'nın bir vsIX paketi bildirim dosyasını nasıl değiştiren ve bir uygulama uzantısı için yükleme davranışını ayar Visual Studio öğrenin.
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
ms.workload:
- vssdk
ms.openlocfilehash: baea7be60c67f186da2372c4644366b4a1a7a202
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905195"
---
# <a name="vsix-manifest-designer"></a>VSIX Bildirim Tasarımcısı
Bir VSIX paketi bildirim dosyasını değiştiren ve bir uygulama uzantısının yükleme davranışını Visual Studio ayarlar.

 **VSIX Bildirim Tasarımcısı,** temel VSIX şemasıyla eşler. Şemada her öğe, tasarımcıda karşılık gelen bir denetim kullanılarak ayarlanır. Şema hakkında daha fazla bilgi için bkz. [VSIX Uzantı Şeması 2.0 Başvurusu.](../extensibility/vsix-extension-schema-2-0-reference.md)

 VSIX Bildirim **Tasarımcısını açmak** için, dosyanın içinde bir *source.extension.vsixmanifest* **Çözüm Gezgini** bulun ve dosyasını açın. Dosya geçerli bir XML içeriyorsa, bildirim tasarımcısı açılmaz.

> [!NOTE]
> *Source.extension.vsixmanifest* dosyası, paket *7.000.000'den sonra extension.vsixmanifest* dosyasına çıktı olarak gelir.

## <a name="uielement-list"></a>UIElement listesi
 **VSIX Bildirim Tasarımcısı,** şemanın bu üst düzey öğelerine karşılık gelen dört bölüm içerir:

- Meta veri

- Hedefleri Yükleme

- Varlıklar

- Bağımlılıklar

  Başlık alanı aşağıdaki denetimleri içerir.

  **Ürün Adı** Uzantı adını açıklar.

  **Ürün Kimliği** Bu paket için benzersiz kimlik bilgilerini belirtir.

  **Yazar** Uzantının yazarının adını belirtir.

  **Sürüm** Uzantının sürüm numarasını belirtir.

  Meta **Veriler** sekmesi aşağıdaki denetimleri içerir.

  **Açıklama** Uzantı Yöneticisi'nde görüntülenecek uzantının metin **açıklamasını sağlar.**

  **Dil** Bildirimde metin verilerine karşılık gelen paket için varsayılan dili belirtir. özniteliği, en-us, en, fr-fr gibi kaynak derlemeleri için ortak dil çalışma zamanı `Language` (CLR) yerel kod kuralına uygun olur. Varsayılan olarak, değer nötrdür, yani paketin herhangi bir dil sürümünde Visual Studio.

  **Lisans** Varsa, kullanıcı lisansını içeren metin dosyasını belirtir.

  **Simge** Bir simge varsa,*Uzantı* Yöneticisi'nde *görüntülenecek simgeyi* içeren grafik dosyasını (.png,.bmp, *.jpeg*, *.ico)* belirtir. Simge resmi 32x32 piksel olmalıdır veya bu boyutlara yeniden boyutlandırılır. Simge belirtilmezse Uzantı **Yöneticisi varsayılan** bir simge kullanır.

  **Önizleme resmi** Bir önizleme görüntüsü *varsa,* Uzantı Yöneticisi'nde görüntülenecek önizleme görüntüsünü içeren grafik dosyasını (.png,  *.bmp*, *.jpeg*, *.ico)* belirtir. Önizleme görüntüsü 200x200 piksel olmalıdır. Önizleme görüntüsü belirtilmezse Uzantı **Yöneticisi varsayılan** bir görüntü kullanır.

  **Etiketler** Arama ipuçları için kullanılacak metin etiketlerini ekler.

  **Sürüm Notları** Sürüm notlarını içeren *bir dosya (.txt*, *.rtf*) belirtir. Ayrıca, sürüm notlarını görüntüleyen bir web sitesinin URL'sini alır.

  **Başlarken Kılavuzu** Uzantıyı veya *VSIX paketinde*.txthakkında bilgi içeren bir dosya (..txt, *.rtf)* belirtir. Uzantı yüklemesi tamamlandığında bu kılavuz görünür. Ayrıca kılavuzu görüntüleyen bir web sitesinin URL'sini alır.

  **Daha Fazla Bilgi URL'si** Ürün hakkında ek bilgi içeren bir web sitesinin URL'sini belirtir.

  Yükleme **Hedefleri sekmesi** aşağıdaki denetimleri içerir.

  **Yükleme türü** Uzantı Visual Studio **SDK'sı hedef yükleme** türleri olarak listele.  Seçenekler, seçtiğiniz türe bağlı olarak farklılık gösterir.

  **Visual Studio Uzantısı** Paketin nasıl yükleneblir ve bu uzantının hangi ürünlere Visual Studio **InstallationTarget** öğelerini listeler. Her ürün, ad ve sürüm veya sürüm aralığına göre ayrı olarak tanımlanır. Ürünler listeye eklenebilir, değiştirilebilir ve silinebilir. Bir ürünün adı ve sürümü,  ilişkili **InstallationTarget** öğesinin Id ve **Version** özniteliklerine karşılık geldi.

  **Sürüm Aralığı** [12.0, 14.0] ve aşağıdaki ifadeyi kullanır:

- [ - en düşük sürüm dahil

- ] - en fazla sürüm dahil

- ( - en düşük sürüme özel

- ) - en yüksek sürüm dış

- Tek sürüm # - yalnızca belirtilen sürüm

  **Uzantı SDK'sı** Belirli bir ürün ve sürüm kapsamına sahip olmayan genel bir yükleme belirtir. **Hedef Platform** Tanımlayıcısı, hedefledkniz "Windows" gibi bir platformdur. **Hedef Platform Sürümü,** hedef platformunun 8.0 gibi bir sürümüdür. **SDK Adı** **ve SDK Sürümü** sırasıyla SDK'nın adı ve sürüm numarasıdır.

  **Bu VSIX tüm kullanıcılar için yüklenir (yüklemede yükseltme gerektirir)** Bu onay kutusunu işaretle, uzantı tüm kullanıcılar için yüklenir; aksi takdirde, yalnızca geçerli kullanıcı için yüklenir.

  **Bu VSIX, Windows Installer** Bu onay kutusunu işaretle, uzantı Windows Installer *(*.msidosyası); aksi takdirde, tipik bir VSIX paketi (*.vsix dosyası) olarak* yüklenir.

  Varlıklar **sekmesi** aşağıdaki denetimleri içerir.

  **Varlık listesi** Bu paketin ortaya çıkar olduğu uzantıyı veya içerik öğelerini açıklayan Varlık öğelerini listeler. Her uzantı veya içerik öğesi kaynak, tür ve yola göre ayrı olarak listelenir. Uzantılar ve içerik öğeleri listeye eklenebilir, değiştirilebilir ve silinebilir. Uzantı veya içerik öğesinin türü ve yolu, ilişkili öğenin `Type` `Path` ve özniteliklerine karşılık `Asset` gelen. Aşağıdaki türler bilinir:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Varlık eklemek veya düzenlemek için varlık türünü, varlığın geçerli çözümde bir proje mi yoksa dosya sisteminde bir dosya mı olduğunu ve projenin adını belirtmeniz gerekir. Ayrıca, ekli olacak klasörün adını da belirtebilirsiniz.

  Ayrıca kendi türlerinizi oluşturabilir ve onlara benzersiz adlar vesiniz.

  Bağımlılıklar **sekmesi** aşağıdaki denetimleri içerir.

  **Ad, Kaynak ve Sürüm Aralığı** Bu paketin bağımlılık öğelerini listeler ve bu pakete bağımlı olan diğer paketlerdir. Bir bağımlılık paketi belirtilirse, bu paket yüklenmeden önce yükilmelidir; aksi takdirde, bu paketin yüklemesi gerekir.

  Bağımlılık paketleri tanımlayıcı, ad, sürüm aralığı, kaynak ve bağımlılığın nasıl çözülecekleri ile belirtilir. Her bağımlılık paketi ad, sürüm ve kaynak tarafından ayrı olarak listelenir. Bağımlılık paketleri listeye eklenebilir, değiştirilebilir ve silinebilir.

  Tanımlayıcı, bağımlılık paketi `ID` meta verisi özniteliğiyle eşleşmeli. Kaynak, geçerli çözümde bulunan bir proje, şu anda yüklü olan bir uzantı veya dosya olabilir. Bağımlılık **nasıl çözümlenir ayarı** iç içe bir paketin göreli yolu veya bağımlılık için indirme konumunun URL'si olabilir. Kimlik, sürüm ve bağımlılık paketinin çözümü ilişkili öğenin `Id` `Version` , ve `Location` özniteliklerine karşılık `Dependency` gelen.

## <a name="see-also"></a>Ayrıca bkz.
- [VSIX uzantı şeması 2.0 başvurusu](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
