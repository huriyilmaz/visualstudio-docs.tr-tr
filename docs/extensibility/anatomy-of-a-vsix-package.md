---
title: VSIX Paketinin Anatomisi | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8a6d3f994c531bd36ab4281c5f0b27e993cd3392
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740085"
---
# <a name="anatomy-of-a-vsix-package"></a>VSIX paketinin anatomisi
VSIX paketi, Visual Studio'nun uzantıları sınıflandırmak ve yüklemek için kullandığı meta verilerle birlikte bir veya daha fazla Visual Studio uzantısı içeren bir *.vsix* dosyasıdır. Bu meta veriler VSIX manifestosunda ve *[Content_Types].xml* dosyasında bulunur. Bir VSIX paketi, yerelleştirilmiş kurulum metni sağlamak için bir veya daha fazla *Extension.vsixlangpack* dosyası içerebilir ve bağımlılıkları yüklemek için ek VSIX paketleri içerebilir.

 VSIX paket formatı Açık Ambalaj Sözleşmeleri (OPC) standardını izler. Paket, *[Content_Types].xml* dosyası ve *.vsix* manifesto dosyası yla birlikte ikili dosyalar ve destekleyici dosyalar içerir. Bir VSIX paketi, birden çok projenin çıktısını, hatta kendi manifestolarına sahip birden çok paketin çıktısını içerebilir.

> [!NOTE]
> VSIX paketlerinde yer alan dosyaların adları, [ \[RFC2396\]](https://www.rfc-editor.org/rfc/rfc2396.txt)altında tanımlandığı şekilde, tek düzen kaynak tanımlayıcılarında (URI) ayrılmış boşlukları veya karakterleri içermemelidir.

## <a name="the-vsix-manifest"></a>VSIX manifestosu
 VSIX bildirimi yüklenecek uzantı hakkında bilgi içerir ve VSX Şeması'nı izler. Daha fazla bilgi için [VSIX uzantı şeması 1.0 referansına](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)bakın. Örnek bir VSIX bildirimi için bkz: [PackageManifest öğesi (kök öğesi, VSX şeması)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

 VSIX bildirimi ^.vsix* dosyasına eklendiğinde adlandırılmalıdır. `extension.vsixmanifest`

## <a name="the-content"></a>İçerik
 Bir VSIX paketi şablonlar, araç kutusu öğeleri, VSPackages veya Visual Studio tarafından desteklenen başka bir uzantı türü içerebilir.

## <a name="language-packs"></a>Dil paketleri
 Bir VSIX paketi yükleme sırasında yerelleştirilmiş metin sağlamak için bir veya daha fazla *Extension.vsixlangpack* dosyaları içerebilir. Daha fazla bilgi için [VSIX paketlerini yerelleştirme'ye](../extensibility/localizing-vsix-packages.md)bakın.

## <a name="dependencies-and-references"></a>Bağımlılıklar ve referanslar
 Bir VSIX paketi referans olarak diğer VSIX paketleri içerebilir. Bu diğer paketlerin her biri kendi VSIX manifestosu içermelidir.

 Bir kullanıcı bağımlılıkları olan bir uzantı yüklemeye çalışırsa, yükleyici gerekli derlemelerin kullanıcı sistemine yüklenmiş olduğunu doğrular. Gerekli derlemeler bulunamazsa, **Uzantılar ve Güncelleştirmeler** eksik derlemelerin listesini görüntüler.

 Uzantı bildirimi bir veya daha fazla [Başvuru](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) öğesi içeriyorsa, **Uzantılar ve Güncelleştirmeler** her başvurunun bildirimini sistemde yüklü olan uzantılarla karşılaştırır ve zaten yüklü değilse başvurulan uzantıyı yükler. Başvurulan uzantının önceki bir sürümü yüklenirse, yeni sürüm bunun yerine yeni sürüm yüklenir.

 Çok projeli bir çözümdeki bir proje, aynı çözümdeki başka bir projeye başvuru içeriyorsa, VSIX paketi bu projenin bağımlılıklarını içerir. İç proje için başvuruyu tıklatarak ve ardından **Özellikler** penceresinde VSIX özelliğine **dahil olan Çıktı Gruplarını** `BuiltProjectOutputGroup`'da ' olarak ayarlayarak bu davranışı geçersiz kılabilirsiniz.

 VSIX paketine başvurulan derlemelerden uydu DL'lerini `SatelliteDllsProjectOutputGroup` eklemek için **VSIX özelliğine dahil olan Çıkış Gruplarına** ekleyin.

## <a name="installation-location"></a>Yükleme konumu
 Yükleme sırasında **Uzantılar ve Güncelleştirmeler,** VSIX paketinin içeriğini *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*altında bir klasörde arar.

 Varsayılan olarak, *%LocalAppData%* kullanıcıya özgü bir dizini olduğundan, yükleme yalnızca geçerli kullanıcı için geçerlidir. Ancak, bildirimin [AllUsers](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) öğesini `True`ayarlarsanız, uzantısı altında yüklenir <em>... \\ </em>VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> ve bilgisayarın tüm kullanıcıları tarafından kullanılabilir.

## <a name="content_typesxml"></a>[Content_Types].xml
 *[Content_Types].xml* dosyası genişletilmiş *.vsix* dosyasındaki dosya türlerini tanımlar. Visual Studio paketin yüklenmesi sırasında bu dosyayı kullanır, ancak dosyanın kendisini yüklemez. Bu dosya hakkında daha fazla bilgi için [bkz: [Content_types].xml dosyasının yapısı.](the-structure-of-the-content-types-dot-xml-file.md)

 Açık Ambalaj Sözleşmeleri (OPC) standardı na göre *bir [Content_Types].xml* dosyası gereklidir. OPC hakkında daha fazla bilgi için Bkz. [OPC: Verilerinizi](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) MSDN Web sitesinde paketlemek için yeni bir standart.
