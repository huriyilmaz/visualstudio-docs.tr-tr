---
title: Dosya Özellikleri, JavaScript
ms.date: 06/21/2017
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- javascript.project.property.expandedsdknode.fileversion
- javascript.project.property.expandedsdknode.uri
- javascript.project.property.expandedsdknode.filename
- javascript.project.property.reference.description
- javascript.project.property.reference.specificversion
- javascript.project.property.reference.identity
- javascript.project.property.fullpath
- javascript.project.property.packageaction
- javascript.project.property.reference.package
- javascript.project.property.copytooutputdirectory
- javascript.project.property.expandedsdknode.sdkpath
- javascript.project.property.reference.filetype
- javascript.project.property.reference.culture
- javascript.project.property.filename
- javascript.project.property.reference.resolvedpath
- javascript.project.property.reference.version
ms.assetid: 085913b8-a97b-45f7-85fa-bbb0902f3ee9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b27f103b2431914efbd22c119e11221b5814dae4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926228"
---
# <a name="file-properties-javascript"></a>Dosya Özellikleri, JavaScript

Proje sisteminin dosyalarda hangi eylemleri gerçekleştirmesi gerektiğini belirtmek için dosya özelliklerini kullanabilirsiniz. Örneğin, dosyanın pakete kaynak dosyası olarak eklenip eklenmemesi gerektiğini gösterecek şekilde dosya özellikleri ayarlayabilirsiniz.

Çözüm Gezgini'nde herhangi bir dosyayı seçebilir ve özellikler penceresindeki özelliklerini inceleyebilirsiniz. JavaScript dosyalarının dört özelliği vardır: Çıktı Dizini, **Paket Eylem,** **Dosya Adı**ve **Dosya Yolu'na** **kopyalayın.**

## <a name="file-properties"></a>Dosya Özellikleri
Bu bölümde JavaScript dosyalarında ortak özellikler açıklanmaktadır.

### <a name="copy-to-output-directory-property"></a>Çıktı Dizin Özelliğine Kopyala
Bu özellik, seçili kaynak dosyanın çıktı dizinine kopyalanacağı koşulları belirtir. Dosya **Do not copy** çıkış dizinine kopyalanmayacaksa kopyalamayın'ı seçin. Dosya her zaman çıktı dizinine kopyalanacaksa **Her zaman Kopyala'yı** seçin. Dosya **Copy if newer** yalnızca çıktı dizininde aynı adı taşıyan varolan bir dosyadan daha yeni olduğunda kopyalanacaksa kopyala'yı seçin.

### <a name="package-action"></a>Paket Eylem
**Paket Eylem** özelliği, bir yapı yürütüldüğünde Visual Studio'nun bir dosyayla ne yaptığını gösterir. **Paket Eylem** birkaç değerden biri olabilir:

- **Yok** - Dosya paket manifestosuna dahil değildir. Örnek, Readme dosyası gibi belgeler içeren bir metin dosyasıdır.

- **İçerik** - Dosya paket manifestosuna dahildir. Örneğin, bu ayar .htm, .js, .css, görüntü, ses veya video dosyası nın varsayılan değeridir.

- **Manifest** - Dosya paket manifestosuna dahil değildir. Bunun yerine, paket bildirimi oluştururken dosya giriş için kullanılır. Bu, package.appxmanifest dosyasının varsayılan değeridir.

- **Kaynak** - Dosya paket bildirimine dahil değildir. Bunun yerine, dosyanın içeriği paket bildirimine giren Paket Kaynak Dizini'nde (PRI) dizine dizine işlenir. Genellikle kaynak dosyaları için kullanılır.

**Paket Eylemi** için varsayılan değer, çözüme eklediğiniz dosyanın uzantısına bağlıdır.

### <a name="file-name-property"></a>Dosya Adı Özelliği
Dosya adını salt okunur değer olarak görüntüler. Dosyayı yeniden adlandırmak için Solution Explorer'da sağ tıklatmanız ve **Yeniden Adlandır'ı seçmeniz**gerekir.

### <a name="full-path-property"></a>Tam Yol Özelliği
Dosyaya giden tam yolu salt okunur değer olarak görüntüler. Dosyanın yolunu değiştirmek için, Solution Explorer'da dosyayı sürükleyip bırakabilirsiniz.

## <a name="reference-file-properties"></a>Başvuru Dosyası Özellikleri
Bu bölümde, JavaScript kullanılarak oluşturulmuş bir UWP uygulamasından başvurulan dosyalara yaygın özellikler açıklanmaktadır. .winmd dosyası, SDK başvurusu, projeden projeye başvuru veya Çözüm Gezgini'nde bir derleme başvurusu gibi bir başvuru seçtiğinizde, dosya türüne göre Özellikler penceresinde başka özellikler görüntülenebilir.

### <a name="culture"></a>Kültür
Başvuruyla ilişkili dili görüntüler.

### <a name="file-type"></a>Dosya Türü
Başvurunun dosya türünü görüntüler.

### <a name="file-version"></a>Dosya Sürümü
Başvurunun dosya sürümünü görüntüler.

### <a name="identity"></a>Kimlik
Proje dosyasında depolanan projede kullanılan başvurunun kimliğini görüntüler.

### <a name="package"></a>Paket
Başvuruyla ilişkili paket manifestosunun adını görüntüler.

### <a name="resolved-path"></a>Çözümlenmiş Yol
Projede kullanılan başvuruyolunu görüntüler.

### <a name="sdk-path"></a>SDK Yolu
Başvurulan SDK dosyasına giden yolu görüntüler.

### <a name="uri"></a>Urı
Dosyayı kaynak dosya olarak eklemek için projenin HTML veya JavaScript dosyalarına eklenmesi gereken URI'yi görüntüler.

### <a name="version"></a>Sürüm
Başvurunun sürümünü görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve Çözüm Özelliklerini Yönetme](../../ide/managing-project-and-solution-properties.md)