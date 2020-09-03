---
title: VSıX paketinin anatomumu | Microsoft Docs
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
ms.openlocfilehash: c52f87426b9f06ad40d77c2cc9e7be1627d2c82d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88250822"
---
# <a name="anatomy-of-a-vsix-package"></a>VSıX paketinin anatomumu
VSıX paketi, Visual Studio 'Nun uzantıları sınıflandırmak ve yüklemek için kullandığı meta verilerle birlikte bir veya daha fazla Visual Studio uzantısı içeren bir *. VSIX* dosyasıdır. Bu meta veriler VSıX bildiriminde ve *[Content_Types]. xml* dosyasında bulunur. Bir VSıX paketi ayrıca yerelleştirilmiş kurulum metni sağlamak için bir veya daha fazla *extension. valtlangpack* dosyası içerebilir ve bağımlılıkları yüklemek IÇIN ek VSIX paketleri içerebilir.

 VSıX paketi biçimi açık paketleme kuralları (OPC) standardını izler. Paket, bir *[Content_Types]. xml* dosyası ve bir *. vsix* bildirim dosyası ile birlikte ikili dosyaları ve destekleyici dosyaları içerir. Bir VSıX paketi birden çok projenin çıkışını ya da kendi bildirimlerine sahip birden çok paketi içerebilir.

> [!NOTE]
> VSıX paketlerine dahil edilen dosyaların adları, [ \[ rfc2396 \] ](https://www.rfc-editor.org/rfc/rfc2396.txt)altında tanımlandığı gibi Tekdüzen Kaynak tanımlayıcılarında (URI) ayrılan boşluk veya karakterleri içermemelidir.

## <a name="the-vsix-manifest"></a>VSıX bildirimi
 VSıX bildirimi yüklenecek uzantı hakkında bilgiler içerir ve VSX şemasını izler. Daha fazla bilgi için bkz. [VSIX uzantı şeması 1,0 başvurusu](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b). Örnek VSıX bildirimi için bkz. [PackageManifest öğesi (root öğesi, VSX şeması)](https://msdn.microsoft.com/library/f8ae42ba-775a-4d2b-976a-f556e147f187).

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
 Yükleme sırasında, **Uzantılar ve güncelleştirmeler** , VSIX paketinin içeriğini *%LocalAppData%\Microsoft\VisualStudio\14.0\Extensions*altındaki bir klasörde arar.

 Varsayılan olarak, yükleme yalnızca geçerli kullanıcı için geçerlidir, çünkü *% LocalAppData%* kullanıcıya özgü bir dizindir. Ancak, bildirimin [ALLUSERS](https://msdn.microsoft.com/library/ac817f50-3276-4ddb-b467-8bbb1432455b) öğesini olarak ayarlarsanız `True` , uzantı altına yüklenir <em>. \\ </em> VisualStudioInstallationFolder<em>\Common7\IDE\Extensions</em> ve bilgisayarın tüm kullanıcıları tarafından kullanılabilir.

## <a name="content_typesxml"></a>[Content_Types]. xml
 *[Content_Types]. xml* dosyası Genişletilmiş *. vsix* dosyasındaki dosya türlerini tanımlar. Visual Studio, paketin yüklenmesi sırasında bu dosyayı kullanır, ancak dosyanın kendisini yüklemez. Bu dosya hakkında daha fazla bilgi için bkz. [[Content_Types]. xml dosyasının yapısı](the-structure-of-the-content-types-dot-xml-file.md).

 Açık paketleme kuralları (OPC) standardı için bir *[Content_Types]. xml* dosyası gereklidir. OPC hakkında daha fazla bilgi için bkz. [OPC: msdn Web sitesinde verilerinizi paketlemeye yönelik yeni bir standart](https://blogs.msdn.microsoft.com/msdnmagazine/2007/08/08/opc-a-new-standard-for-packaging-your-data/) .
