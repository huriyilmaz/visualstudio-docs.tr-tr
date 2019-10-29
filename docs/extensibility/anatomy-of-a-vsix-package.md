---
title: VSıX paketinin anatomumu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d215849036e76cb51080775f5ea55e1eb0b28c56
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981684"
---
# <a name="anatomy-of-a-vsix-package"></a>VSıX paketinin anatomumu
VSıX paketi, Visual Studio 'Nun uzantıları sınıflandırmak ve yüklemek için kullandığı meta verilerle birlikte bir veya daha fazla Visual Studio uzantısı içeren bir *. VSIX* dosyasıdır. Bu meta veriler VSıX bildiriminde ve *[Content_Types]. xml* dosyasında bulunur. Bir VSıX paketi ayrıca yerelleştirilmiş kurulum metni sağlamak için bir veya daha fazla *extension. valtlangpack* dosyası içerebilir ve bağımlılıkları yüklemek IÇIN ek VSIX paketleri içerebilir.

 VSıX paketi biçimi açık paketleme kuralları (OPC) standardını izler. Paket, bir *[Content_Types]. xml* dosyası ve bir *. vsix* bildirim dosyası ile birlikte ikili dosyaları ve destekleyici dosyaları içerir. Bir VSıX paketi birden çok projenin çıkışını ya da kendi bildirimlerine sahip birden çok paketi içerebilir.

> [!NOTE]
> VSıX paketlerine dahil edilen dosyaların adları, [\[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt)altında tanımlandığı gibi Tekdüzen Kaynak tanımlayıcılarında (URI) ayrılan boşluk veya karakterleri içermemelidir.

## <a name="the-vsix-manifest"></a>VSıX bildirimi
 VSıX bildirimi yüklenecek uzantı hakkında bilgiler içerir ve VSX şemasını izler. Daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Örnek VSıX bildirimi için bkz. [PackageManifest öğesi (root öğesi, VSX şeması)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 VSıX bildirimi, bir ^. VSIX * dosyasına dahil edildiğinde `extension.vsixmanifest` olarak adlandırılmalıdır.

## <a name="the-content"></a>İçerik
 Bir VSıX paketi, Visual Studio tarafından desteklenen şablonlar, araç kutusu öğeleri, VSPackages veya diğer uzantı türlerini içerebilir.

## <a name="language-packs"></a>Dil paketleri
 Bir VSıX paketi, yükleme sırasında yerelleştirilmiş metin sağlamak için bir veya daha fazla *extension. valtlangpack* dosyası içerebilir. Daha fazla bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Bağımlılıklar ve başvurular
 VSıX paketi, diğer VSıX paketlerini başvuru olarak içerebilir. Bu diğer paketlerin her biri kendi VSıX bildirimini içermelidir.

 Bir Kullanıcı bağımlılıkları olan bir uzantıyı yüklemeye çalışırsa, yükleyici gerekli derlemelerin Kullanıcı sisteminde yüklü olduğunu doğrular. Gerekli derlemeler bulunamazsa, **Uzantılar ve güncelleştirmeler** eksik derlemelerin bir listesini görüntüler.

 Uzantı bildirimi bir veya daha fazla [başvuru](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) öğesi Içeriyorsa, **Uzantılar ve güncelleştirmeler** , her başvurunun bildirimini sistemde yüklü olan uzantılara göre karşılaştırır ve henüz yoksa başvurulan uzantıyı yüklerse yüklendiyse. Başvurulan bir uzantının önceki bir sürümü yüklüyse, yeni sürüm yerini alır.

 Çoklu proje çözümündeki bir proje aynı çözümdeki başka bir projeye başvuru içeriyorsa, VSıX paketi o projenin bağımlılıklarını içerir. İç proje başvurusuna tıklayarak ve ardından **Özellikler** penceresinde **VSIX özelliğinde bulunan çıkış gruplarını** `BuiltProjectOutputGroup`olarak ayarlayarak bu davranışı geçersiz kılabilirsiniz.

 VSıX paketindeki başvurulan derlemelerden uydu dll 'Leri eklemek için, **VSIX özelliğinde bulunan çıkış gruplarına** `SatelliteDllsProjectOutputGroup` ekleyin.

## <a name="installation-location"></a>yükleme konumu
 Yükleme sırasında, **Uzantılar ve güncelleştirmeler** , VSIX paketinin içeriğini *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*altındaki bir klasörde arar.

 Varsayılan olarak, yükleme yalnızca geçerli kullanıcı için geçerlidir, çünkü *% LocalAppData%* kullanıcıya özgü bir dizindir. Ancak, bildirimin [ALLUSERS](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) öğesini `True`olarak ayarlarsanız, uzantı <em>..\\</em>VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> altına yüklenir ve bilgisayarın tüm kullanıcıları tarafından kullanılabilir.

## <a name="content_typesxml"></a>[Content_Types]. xml
 *[Content_Types]. xml* dosyası Genişletilmiş *. vsix* dosyasındaki dosya türlerini tanımlar. Visual Studio, paketin yüklenmesi sırasında bu dosyayı kullanır, ancak dosyanın kendisini yüklemez. Bu dosya hakkında daha fazla bilgi için bkz. [[Content_Types]. xml dosyasının yapısı](the-structure-of-the-content-types-dot-xml-file.md).

 Açık paketleme kuralları (OPC) standardı için bir *[Content_Types]. xml* dosyası gereklidir. OPC hakkında daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) .