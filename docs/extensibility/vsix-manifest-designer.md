---
title: VSIX Manifesto Tasarımcısı | Microsoft Dokümanlar
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697889"
---
# <a name="vsix-manifest-designer"></a>VSIX Bildirim Tasarımcısı
Visual Studio uzantısı için yükleme davranışını ayarlayan vsix paket bildirimi dosyasını değiştirir.

 **VSIX Manifest Designer** temel VSIX şemasına göre haritalar. Şemadaki her öğe, tasarımcıda karşılık gelen bir denetim kullanılarak ayarlanabilir. Şema hakkında daha fazla bilgi için [VSIX Extension Schema 2.0 Reference'a](../extensibility/vsix-extension-schema-2-0-reference.md)bakın.

 **VSIX Manifest Designer'ı**açmak için Solution *Explorer'da source.extension.vsixmanifest* dosyasını bulun ve dosyayı açın. **Solution Explorer** Dosya geçerli XML içermiyorsa, bildirim tasarımcısı açılmaz.

> [!NOTE]
> *Source.extension.vsixmanifest* dosyası, paket oluşturulunca *extension.vsixmanifest'e* çıktı.

## <a name="uielement-list"></a>UIElement listesi
 **VSIX Manifest Designer** şemanın bu üst düzey öğelerine karşılık gelen dört bölümden oluşur:

- Meta Veriler

- Hedefleri Yükleyin

- Varlıklar

- Bağımlılıklar

  Başlık alanı aşağıdaki denetimleri içerir.

  **Ürün Adı** Uzantı adını açıklar.

  **Ürün Kimliği** Bu paket için benzersiz kimlik bilgilerini belirtir.

  **Yazar** Uzantının yazarının adını belirtir.

  **Sürüm** Uzantının sürüm numarasını belirtir.

  **Meta veri** sekmesi aşağıdaki denetimleri içerir.

  **Açıklama** **Uzantı Yöneticisi'nde**görüntülenecek uzantının metin açıklamasını sağlar.

  **Dil** Paket için varsayılan dili belirtir, bu da bildirimdeki metin verilerine karşılık gelir. Öznitelik, `Language` kaynak derlemeleri için ortak dil çalışma zamanı (CLR) yerel kod kuralını izler, örneğin, en-us, en, fr-fr. Varsayılan olarak, değer nötrdür, bu da paketin Visual Studio'nun herhangi bir dil sürümünde çalışacağı anlamına gelir.

  **Lisans** Varsa, kullanıcı lisansını içeren metin dosyasını belirtir.

  **Simge** **Uzanım Yöneticisi'nde**görüntülenecek simgeyi içeren grafik dosyasını (*.png*, *.bmp*, *.jpeg*, *.ico*) belirtir, bir simge varsa. Simge görüntüsü 32x32 piksel olmalıdır veya bu boyutlara yeniden boyutlandırılır. Simge belirtilmemişse, **Uzantı Yöneticisi** varsayılan bir simge kullanır.

  **Önizleme görüntüsü** **Uzanım Yöneticisi'nde**görüntülenecek önizleme görüntüsünü içeren grafik dosyasını (*.png*, *.bmp*, *.jpeg*, *.ico*) belirtir, önizleme görüntüsü varsa. Önizleme görüntüsü 200x200 piksel olmalıdır. Önizleme görüntüsü belirtilmemişse, **Uzantı Yöneticisi** varsayılan bir görüntü kullanır.

  **Etiketler** Arama ipuçları için kullanılacak metin etiketleri ekler.

  **Yayın Notları** Sürüm notları içeren bir dosyayı (*.txt*, *.rtf*) belirtir. Ayrıca, sürüm notlarını görüntüleyen bir web sitesinin URL'sini alır.

  **Başlangıç Kılavuzu** VSIX paketinde uzantınveya içeriğin nasıl kullanılacağı hakkında bilgi içeren bir dosyayı (*.txt*, *.rtf)* belirtir. Bu kılavuz, uzantı yükleme tamamlandığında görüntülenir. Ayrıca, kılavuzu görüntüleyen bir web sitesinin URL'sini alır.

  **Daha Fazla Bilgi URL'si** Ürün hakkında ek bilgiler içeren bir web sitesinin URL'sini belirtir.

  **Hedefleri Yükle** sekmesi aşağıdaki denetimleri içerir.

  **Yükleme türü** **Visual Studio Extension** ve Extension **SDK'yı** hedef yükleme türleri olarak listeler. Seçenekler, seçtiğiniz türe bağlı olarak farklıdır.

  **Görsel Stüdyo Uzantısı** Paketin nasıl yüklenebileceğini ve visual studio ürünlerinin hangi uzantının yüklenebileceğini açıklayan **InstallationTarget** öğelerini listeler. Her ürün ada ve bir sürüm veya sürüm aralığına göre ayrı ayrı tanımlanır. Ürünler listeye eklenebilir, değiştirilebilir ve silinebilir. Bir ürünün adı ve sürümü, ilişkili **InstallationTarget** öğesinin **Id** ve **Sürüm** özniteliklerine karşılık gelir.

  **Sürüm Aralığı** [12.0, 14.0] ve aşağıdaki gösterimi kullanır:

- [ - minimum sürüm dahil

- ] - maksimum sürüm dahil

- ( - minimum sürüm özel

- ) - maksimum sürüm özel

- Tek sürüm # - sadece belirtilen sürüm

  **Uzatma SDK** Belirli bir ürün ve sürüm kapsamına giren genel bir yükleme belirtir. **Hedef Platform Tanımlayıcı,** hedeflediğiniz "Windows" gibi platformdur. **Hedef Platform Sürümü,** hedef platformunuzun 8.0 gibi sürümüdür. **SDK Adı** ve **SDK Sürümü,** sırasıyla SDK'nın adı ve sürüm numarasıdır.

  **Bu VSIX tüm kullanıcılar için yüklenir (yükleme de yükseklik gerektirir)** Bu onay kutusunu seçerseniz, uzantı tüm kullanıcılar için yüklenir; aksi takdirde, yalnızca geçerli kullanıcı için yüklenir.

  **Bu VSIX Windows Installer tarafından yüklenir** Bu onay kutusunu seçerseniz, uzantı Windows Installer *(.msi* dosyası) tarafından yüklenir; aksi takdirde, tipik bir VSIX paketi *(.vsix* dosyası) olarak yüklenir.

  **Varlıklar** sekmesi aşağıdaki denetimleri içerir.

  **Varlıkların listesi** Bu paketin yüzer olduğu uzantı veya içerik öğelerini açıklayan Varlık öğelerini listeler. Her uzantı veya içerik öğesi kaynak, tür ve yola göre ayrı ayrı listelenir. Uzantılar ve içerik öğeleri listeye eklenebilir, değiştirilebilir ve silinebilir. Bir uzantı veya içerik öğesinin türü `Type` ve `Path` yolu ilişkili `Asset` öğenin ve özniteliklerine karşılık gelir. Aşağıdaki türleri bilinmektedir:

- Microsoft.VisualStudio.Paketi

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Microsoft.VisualStudio.ProjectTemplate

- Microsoft.VisualStudio.ItemTemplate

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Bir kıymet eklemek veya düzenlemek için, kıymetin geçerli çözümde bir proje mi yoksa dosya sistemindeki bir dosya mı olduğunu ve projenin adını varlık türünü belirtmeniz gerekir. Ayrıca, katışdırılacak klasörün adını da belirtebilirsiniz.

  Ayrıca kendi türlerinizi oluşturabilir ve onlara benzersiz adlar verebilirsiniz.

  **Bağımlılıklar** sekmesi aşağıdaki denetimleri içerir.

  **Ad, Kaynak ve Sürüm Aralığı** Bu paketin bağımlılık öğelerini listeler, bu paketin bağlı olduğu diğer paketlerdir. Bağımlılık paketi belirtilmişse, bu paket yüklenmeden önce yüklenmesi gerekir; aksi takdirde, bu paketi yüklemeniz gerekir.

  Bağımlılık paketleri tanımlayıcı, ad, sürüm aralığı, kaynak ve bağımlılığın nasıl çözüleceği ile belirtilir. Her bağımlılık paketi ada, sürüme ve kaynağa göre ayrı ayrı listelenir. Bağımlılık paketleri listeye eklenebilir, değiştirilebilir ve silinebilir.

  Tanımlayıcı bağımlılık paketi meta verilerinözeuygun olmalıdır. `ID` Kaynak, geçerli çözümde bir proje, şu anda yüklü bir uzantı veya dosya olabilir. **Bağımlılık nasıl çözülür** ayarı iç içe bir paketin göreli yolu veya bağımlılık için karşıdan yükleme konumunun URL'si olabilir. Kimlik, sürüm ve bağımlılık paketinin çözünürlüğü ilişkili `Id` `Dependency` `Version`öğenin `Location` , ve özniteliklerine karşılık gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [VSIX uzantı şeması 2.0 referans](../extensibility/vsix-extension-schema-2-0-reference.md)
- [VSIX paketinin anatomisi](../extensibility/anatomy-of-a-vsix-package.md)
