---
title: Dosya Özellikleri, JavaScript
description: Dosya özelliklerini kullanarak proje sisteminin dosyalarda hangi işlemleri yapması gerektiğini belirtebilirsiniz.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: efe1486cf8ac2b64965ed157abbb47dc2d8c7b6c
ms.sourcegitcommit: a7944c325bedd8efbb244452741864089a02f5db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2020
ms.locfileid: "91947797"
---
# <a name="file-properties-javascript"></a>Dosya Özellikleri, JavaScript

Dosya özelliklerini, proje sisteminin dosyalarda hangi işlemleri yapması gerektiğini göstermek için kullanabilirsiniz. Örneğin, dosya özelliklerini, bir dosyanın pakete bir kaynak dosyası olarak eklenip eklenmeyeceğini belirtmek için ayarlayabilirsiniz.

Çözüm Gezgini herhangi bir dosyayı seçip Özellikler penceresi özelliklerini inceleyebilirsiniz. JavaScript dosyaları dört özelliğe sahiptir: **çıkış dizinine**, **paket eylemine**, **dosya adına**ve **dosya yoluna**kopyalayın.

## <a name="file-properties"></a>Dosya özellikleri
Bu bölümde JavaScript dosyaları için ortak olan özellikler açıklanmaktadır.

### <a name="copy-to-output-directory-property"></a>Çıkış dizinine Kopyala özelliği
Bu özellik, seçilen kaynak dosyanın çıkış dizinine kopyalanacağı koşulları belirtir. Dosya çıkış dizinine kopyalanmadıysa **kopyalamayın** ' ı seçin. Dosya her zaman çıkış dizinine kopyalanırsa, **her zaman Kopyala** ' yı seçin. Dosya yalnızca çıkış dizininde aynı ada sahip olan mevcut bir dosyadan daha yeniyse **Kopyala** ' yı seçin.

### <a name="package-action"></a>Paket eylemi
**Paket eylemi** özelliği, bir derleme yürütüldüğünde Visual Studio 'nun bir dosyayla ne yaptığını gösterir. **Paket eylemi** birkaç değerden birine sahip olabilir:

- **Hiçbiri** -dosya paket bildirimine dahil değildir. Örneğin, Benioku dosyası gibi belgeleri içeren bir metin dosyasıdır.

- **İçerik** -dosya paket bildirimine dahildir. Örneğin, bu ayar bir. htm,. js,. css, görüntü, ses veya video dosyası için varsayılan değerdir.

- **Bildirim** -dosya paket bildirimine dahil değildir. Bunun yerine, dosya, paket bildirimi oluşturulurken giriş için kullanılır. Bu, Package. appxmanifest dosyası için varsayılan değerdir.

- **Kaynak** -dosya paket bildirimine dahil değildir. Bunun yerine, dosyanın içeriği paket bildirimine giden paket kaynak dizini (PRı) içinde dizinlenir. Genellikle kaynak dosyaları için kullanılır.

**Paket eylemi** için varsayılan değer çözüme eklediğiniz dosyanın uzantısına bağlıdır.

### <a name="file-name-property"></a>Dosya adı özelliği
Dosya adını salt bir salt okuma değeri olarak görüntüler. Dosyayı yeniden adlandırmak için Çözüm Gezgini ' ye sağ tıklayıp **Yeniden Adlandır**' ı seçmeniz gerekir.

### <a name="full-path-property"></a>Tam yol özelliği
Dosyanın tam yolunu salt okuma değeri olarak görüntüler. Dosyanın yolunu değiştirmek için Çözüm Gezgini dosyayı sürükleyip bırakabilirsiniz.

## <a name="reference-file-properties"></a>Başvuru dosyası özellikleri
Bu bölümde, JavaScript kullanılarak oluşturulan UWP uygulamasından başvurulan dosyalar için ortak özellikler açıklanmaktadır. Bir. winmd dosyası, bir SDK başvurusu, bir projeden projeye başvuru veya Çözüm Gezgini bir derleme başvurusu gibi bir başvuruyu seçtiğinizde, diğer özellikler dosya türüne göre Özellikler penceresi gösterebilir.

### <a name="culture"></a>Kültür
Başvuru ile ilişkili dili görüntüler.

### <a name="file-type"></a>Dosya türü
Başvurunun dosya türünü görüntüler.

### <a name="file-version"></a>Dosya Sürümü
Başvurunun dosya sürümünü görüntüler.

### <a name="identity"></a>Kimlik
Proje dosyasında saklanan, projede kullanılan başvurunun kimliğini görüntüler.

### <a name="package"></a>Paket
Başvuruyla ilişkili paket bildiriminin adını görüntüler.

### <a name="resolved-path"></a>Çözümlenen yol
Projede kullanılan başvurunun yolunu görüntüler.

### <a name="sdk-path"></a>SDK yolu
Başvurulan SDK dosyasının yolunu görüntüler.

### <a name="uri"></a>Kullanılmamışsa
Dosyayı kaynak dosya olarak dahil etmek için projenin HTML veya JavaScript dosyalarına dahil olması gereken URI 'yi görüntüler.

### <a name="version"></a>Sürüm
Başvurunun sürümünü görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve Çözüm Özelliklerini Yönetme](../../ide/managing-project-and-solution-properties.md)