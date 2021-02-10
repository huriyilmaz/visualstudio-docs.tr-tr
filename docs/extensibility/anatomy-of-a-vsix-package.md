---
title: VSıX paketinin anatomumu | Microsoft Docs
description: Visual Studio 'daki bir VSıX paketinin içerikleri, bir veya daha fazla Visual Studio uzantısı ve bir meta veri bildirim dosyası içeren bir dosya hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- visual studio extension
- vsix
- packages
ms.assetid: 8b86d62f-c274-4e91-82e0-38cdb9a423d5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8d25430206129f0236661222b92cefdbe538a7ad
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933576"
---
# <a name="anatomy-of-a-vsix-package"></a>VSıX paketinin anatomumu
VSıX paketi, Visual Studio 'Nun uzantıları sınıflandırmak ve yüklemek için kullandığı meta verilerle birlikte bir veya daha fazla Visual Studio uzantısı içeren bir *. VSIX* dosyasıdır. Bu meta veriler VSıX bildiriminde ve *[Content_Types]. xml* dosyasında bulunur. Bir VSıX paketi ayrıca yerelleştirilmiş kurulum metni sağlamak için bir veya daha fazla *extension. valtlangpack* dosyası içerebilir ve bağımlılıkları yüklemek IÇIN ek VSIX paketleri içerebilir.

 VSıX paketi biçimi açık paketleme kuralları (OPC) standardını izler. Paket, bir *[Content_Types]. xml* dosyası ve bir *. vsix* bildirim dosyası ile birlikte ikili dosyaları ve destekleyici dosyaları içerir. Bir VSıX paketi birden çok projenin çıkışını ya da kendi bildirimlerine sahip birden çok paketi içerebilir.

> [!NOTE]
> VSıX paketlerine dahil edilen dosyaların adları, [ \[ rfc2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt)altında tanımlandığı gibi Tekdüzen Kaynak tanımlayıcılarında (URI) ayrılan boşluk veya karakterleri içermemelidir.

## <a name="the-vsix-manifest"></a>VSıX bildirimi
 VSıX bildirimi yüklenecek uzantı hakkında bilgiler içerir ve VSX şemasını izler. Daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](/previous-versions/dd393700(v=vs.110)). Örnek VSıX bildirimi için bkz. [PackageManifest öğesi (root öğesi, VSX şeması)](/previous-versions/dd393754(v=vs.110)).

 VSıX bildiriminin `extension.vsixmanifest` bir ^. VSIX * dosyasına dahil edildiğinde adlandırılması gerekir.

## <a name="the-content"></a>İçerik
 Bir VSıX paketi, Visual Studio tarafından desteklenen şablonlar, araç kutusu öğeleri, VSPackages veya diğer uzantı türlerini içerebilir.

## <a name="language-packs"></a>Dil paketleri
 Bir VSıX paketi, yükleme sırasında yerelleştirilmiş metin sağlamak için bir veya daha fazla *extension. valtlangpack* dosyası içerebilir. Daha fazla bilgi için bkz. [VSIX paketlerini yerelleştirme](../extensibility/localizing-vsix-packages.md).

## <a name="dependencies-and-references"></a>Bağımlılıklar ve başvurular
 VSıX paketi, diğer VSıX paketlerini başvuru olarak içerebilir. Bu diğer paketlerin her biri kendi VSıX bildirimini içermelidir.

 Bir Kullanıcı bağımlılıkları olan bir uzantıyı yüklemeye çalışırsa, yükleyici gerekli derlemelerin Kullanıcı sisteminde yüklü olduğunu doğrular. Gerekli derlemeler bulunamazsa, **Uzantılar ve güncelleştirmeler** eksik derlemelerin bir listesini görüntüler.

 Uzantı bildirimi bir veya daha fazla [başvuru](/previous-versions/visualstudio/visual-studio-2010/dd393687(v=vs.100)) öğesi Içeriyorsa, **Uzantılar ve güncelleştirmeler** , her başvurunun bildirimini sistemde yüklü olan uzantılara göre karşılaştırır ve henüz yüklenmemişse başvurulan uzantıyı ekler. Başvurulan bir uzantının önceki bir sürümü yüklüyse, yeni sürüm yerini alır.

 Çoklu proje çözümündeki bir proje aynı çözümdeki başka bir projeye başvuru içeriyorsa, VSıX paketi o projenin bağımlılıklarını içerir. İç proje başvurusunu seçerek ve ardından **Özellikler** penceresinde **VSIX özelliğinde bulunan çıkış gruplarını** olarak ayarlayarak bu davranışı geçersiz kılabilirsiniz `BuiltProjectOutputGroup` .

 VSıX paketindeki başvurulan derlemelerden uydu dll 'Leri eklemek için `SatelliteDllsProjectOutputGroup` **VSIX özelliğinde bulunan çıkış gruplarına** ekleyin.

## <a name="installation-location"></a>Yükleme konumu
 Yükleme sırasında, **Uzantılar ve güncelleştirmeler** , VSIX paketinin içeriğini *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions* altındaki bir klasörde arar.

 Varsayılan olarak, yükleme yalnızca geçerli kullanıcı için geçerlidir, çünkü *% LocalAppData%* kullanıcıya özgü bir dizindir. Ancak, bildirimin [ALLUSERS](/previous-versions/ee191547(v=vs.110)) öğesini olarak ayarlarsanız `True` , uzantı altına yüklenir <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> ve bilgisayarın tüm kullanıcıları tarafından kullanılabilir.

## <a name="content_typesxml"></a>[Content_Types]. xml
 *[Content_Types]. xml* dosyası Genişletilmiş *. vsix* dosyasındaki dosya türlerini tanımlar. Visual Studio, paketin yüklenmesi sırasında bu dosyayı kullanır, ancak dosyanın kendisini yüklemez. Bu dosya hakkında daha fazla bilgi için bkz. [[Content_Types]. xml dosyasının yapısı](the-structure-of-the-content-types-dot-xml-file.md).

 Açık paketleme kuralları (OPC) standardı için bir *[Content_Types]. xml* dosyası gereklidir. OPC hakkında daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](/archive/blogs/msdnmagazine/opc-a-new-standard-for-packaging-your-data) .