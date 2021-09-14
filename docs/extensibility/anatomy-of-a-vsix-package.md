---
title: VSIX Paketi Anatomisi | Microsoft Docs
description: Visual Studio'daki VSIX paketinin içeriği, bir veya daha fazla uzantı ve meta veri bildirim Visual Studio dosya hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9485aeba7d531c0a05f33ad759688e9fd05a29f9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725328"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX paketinin anatomisi
VSIX paketi, uzantıları sınıflandırmak ve yüklemek için Visual Studio meta verilerle birlikte bir veya daha fazla Visual Studio *içeren bir .vsix* dosyasıdır. Bu meta veriler VSIX bildiriminde ve *[Content_Types].xml* içerir. Bir VSIX paketi, yerelleştirilmiş kurulum metni sağlamak için bir veya daha fazla *Extension.vsixlangpack* dosyası içerebilir ve bağımlılıkları yüklemek için ek VSIX paketleri içerebilir.

 VSIX paket biçimi Açık Paketleme Kuralları (OPC) standardını izler. Paket, *[Content_Types].xml* dosyası ve *bir .vsix* bildirim dosyasıyla birlikte ikili dosyalar ve destek dosyaları içerir. Bir VSIX paketi, birden çok proje veya hatta kendi bildirimleri olan birden çok paketin çıkışını içerebilir.

> [!NOTE]
> VSIX paketlerinde yer alan dosyaların [ \[ adları, RFC2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt)altında tanımlandığı gibi Tekdü Kaynak Tanımlayıcıları 'da (URI) ayrılmış boşluklar veya karakterler içermemalıdır.

## <a name="the-vsix-manifest"></a>VSIX bildirimi
 VSIX bildirimi, yüklenmek için uzantı hakkında bilgiler içerir ve VSX Şemasını izler. Daha fazla bilgi için bkz. [VSIX uzantı şeması 1.0 başvurusu.](/previous-versions/dd393700(v=vs.110)) Örnek bir VSIX bildirimi için bkz. [PackageManifest öğesi (kök öğe, VSX şeması)](/previous-versions/dd393754(v=vs.110)).

 VSIX bildirimi bir `extension.vsixmanifest` ^.vsix* dosyasına ekli olduğunda adlandırılmış olması gerekir.

## <a name="the-content"></a>İçerik
 VSIX paketi şablonlar, araç kutusu öğeleri, VSPackage'lar veya uygulama tarafından desteklenen başka bir uzantı Visual Studio.

## <a name="language-packs"></a>Dil paketleri
 VsIX paketi, yükleme sırasında yerelleştirilmiş metin sağlamak için bir veya daha fazla *Extension.vsixlangpack* dosyası içerebilir. Daha fazla bilgi için [bkz. VSIX paketlerini yerelleştirme.](../extensibility/localizing-vsix-packages.md)

## <a name="dependencies-and-references"></a>Bağımlılıklar ve başvurular
 VsIX paketi, başvuru olarak başka VSIX paketleri içerebilir. Bu diğer paketlerin her biri kendi VSIX bildirimini içermeli.

 Kullanıcı bağımlılıkları olan bir uzantıyı yüklemeye çalışırsa, yükleyici gerekli derlemelerin kullanıcı sisteminde yüklü olduğunu doğrular. Gerekli derlemeler bulunamasa **Uzantılar ve Güncelleştirmeler** eksik derlemelerin listesini görüntüler.

 Uzantı bildirimi bir veya [](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) daha fazla Başvuru öğeleri içerirse **Uzantılar** ve Güncelleştirmeler, her bir başvuru bildirimini sistemde yüklü olan uzantılar ile karşılaştırıldığında, başvurulan uzantı zaten yüklü değilse yüklenir. Başvurulan uzantının önceki bir sürümü yüklüyse, uzantının yerini daha yeni bir sürüme verir.

 Çok projeli çözümdeki bir proje, aynı çözümdeki başka bir projeye başvuru içerirse VSIX paketi bu projenin bağımlılıklarını içerir. İç proje için başvuru seçerek ve ardından Özellikler penceresinde **VSIX** özelliğine Dahil Edilen Çıkış Grupları ayarını olarak ayarerek bu davranışı geçersiz  kılabilirsiniz. `BuiltProjectOutputGroup`

 VSIX paketinde başvurulan derlemelerden uydu URL'lerini dahil etmek için, `SatelliteDllsProjectOutputGroup` **VSIX özelliğine Dahil Edilen Çıkış Gruplarına** ekleyin.

## <a name="installation-location"></a>Yükleme konumu
 Yükleme sırasında, **Uzantılar** ve Güncelleştirmeler VSIX paketinin *içeriğini %LocalAppData%\Microsoft\VisualStudio\14.0\Extensions* altındaki bir klasörde arama.

 *%LocalAppData%* kullanıcıya özgü bir dizin olduğundan yükleme varsayılan olarak yalnızca geçerli kullanıcı için geçerlidir. Ancak bildirimin [AllUsers öğesini](/previous-versions/ee191547(v=vs.110)) olarak ayarlayacak olursanız `True` uzantı altına <em>yüklenir. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> ve bilgisayarın tüm kullanıcıları tarafından kullanılabilir.

## <a name="content_typesxml"></a>[Content_Types].xml
 *[Content_Types].xml* dosyası, genişletilmiş *.vsix* dosyasındaki dosya türlerini tanımlar. Visual Studio paketin yüklemesi sırasında bu dosyayı kullanır, ancak dosyanın kendisini yüklemez. Bu dosya hakkında daha fazla bilgi için [bkz. [Content_types].xml dosyası.](the-structure-of-the-content-types-dot-xml-file.md)

 *[Content_Types].xml* dosyası, Açık Paketleme Kuralları (OPC) standardı tarafından gereklidir. OPC hakkında daha fazla bilgi için MSDN Web sitesinde [OPC:](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) Verilerinizi paketlemeye ilişkin yeni bir standart konusuna bakın.