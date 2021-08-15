---
title: Dosya Özellikleri, JavaScript
description: Proje sisteminin dosyalar üzerinde hangi eylemleri gerçekleştirmesi gerektiğini belirtmek için dosya özelliklerini kullanmayı öğrenin.
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aae0df927b4544afe275b8cdf056cc45741a3aa3998182cbcf809b3c2b1f6005
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121258921"
---
# <a name="file-properties-javascript"></a>Dosya Özellikleri, JavaScript

Proje sisteminin dosyalar üzerinde hangi eylemleri gerçekleştirmesi gerektiğini belirtmek için dosya özelliklerini kullanabilirsiniz. Örneğin, bir dosyanın pakete kaynak dosyası olarak ek gerekip gerek olmadığını belirtmek için dosya özelliklerini ayarlayın.

Dosyalarda herhangi bir dosyayı Çözüm Gezgini sonra dosyanın özelliklerini Özellikler penceresi. JavaScript dosyalarının dört özelliği vardır: **Çıkış Dizinine Kopyala,** **Paket Eylemi,** **Dosya Adı** ve **Dosya Yolu.**

## <a name="file-properties"></a>Dosya Özellikleri
Bu bölümde JavaScript dosyalarında ortak olan özellikler açık bulunmaktadır.

### <a name="copy-to-output-directory-property"></a>Çıkış Dizini Özelliğine Kopyala
Bu özellik, seçilen kaynak dosyanın çıkış dizinine kopyalanacak koşulları belirtir. Dosya **hiçbir zaman çıkış** dizinine kopyalanmazsa Kopyalama'ya seçin. Dosya **her zaman** çıkış dizinine kopyalanmışsa Her zaman kopyala'yi seçin. Dosya **yalnızca çıkış dizininde** aynı adla mevcut bir dosyadan daha yeni olduğunda kopyalanırsa Daha yenise Kopyala'ya seçin.

### <a name="package-action"></a>Paket Eylemi
Paket **Eylemi özelliği,** bir Visual Studio yürütülürken dosyayla ne yaptığını gösterir. **Paket Eylemi** birkaç değerden birini olabilir:

- **Hiçbiri** - Dosya paket bildirimine dahil değildir. Örneğin, Beni Oku dosyası gibi belgeleri içeren bir metin dosyasıdır.

- **İçerik** - Dosya paket bildirimine dahil edilir. Örneğin, bu ayar bir .htm, .js, .css, görüntü, ses veya video dosyası için varsayılan değerdir.

- **Bildirim** - Dosya paket bildirimine dahil değildir. Bunun yerine dosya, paket bildirimini oluşturmada giriş için kullanılır. Bu, package.appxmanifest dosyası için varsayılan değerdir.

- **Kaynak** - Dosya paket bildirimine dahil değildir. Bunun yerine, dosyanın içeriği paket bildirimine giden Paket Kaynak Dizini'ne (PRI) dizine dahil olur. Genellikle kaynak dosyaları için kullanılır.

Paket Eylemi için **varsayılan** değer, çözüme eklemek istediğiniz dosyanın uzantısına bağlıdır.

### <a name="file-name-property"></a>Dosya Adı Özelliği
Dosya adını salt okunur bir değer olarak görüntüler. Dosyayı yeniden adlandırmak için Dosya'ya sağ tıklar ve Çözüm Gezgini'yi **seçmeniz gerekir.**

### <a name="full-path-property"></a>Tam Yol Özelliği
Dosyanın tam yolunu salt okunur bir değer olarak görüntüler. Dosyanın yolunu değiştirmek için dosyayı sürükleyip dosyanın içine sürükleyip Çözüm Gezgini.

## <a name="reference-file-properties"></a>Başvuru Dosyası Özellikleri
Bu bölümde, JavaScript kullanılarak bir UWP uygulamasından başvurulan dosyalarda ortak özellikler açıklandı. .winmd dosyası, SDK başvurusu, projeden projeye başvuru veya Çözüm Gezgini'daki bir derleme başvurusu gibi bir başvuru seçerek dosya türüne göre Özellikler penceresi'de diğer özellikler görüntülenmeye devam ediyor olabilir.

### <a name="culture"></a>Kültür
Başvuruyla ilişkili dili görüntüler.

### <a name="file-type"></a>Dosya Türü
Başvuru dosya türünü görüntüler.

### <a name="file-version"></a>Dosya Sürümü
Başvuru dosya sürümünü görüntüler.

### <a name="identity"></a>Kimlik
Proje dosyasında depolanan projede kullanılan başvuru kimliğini görüntüler.

### <a name="package"></a>Paket
Başvuruyla ilişkili paket bildiriminin adını görüntüler.

### <a name="resolved-path"></a>Çözümlenen Yol
Projede kullanılan başvuru yolunu görüntüler.

### <a name="sdk-path"></a>SDK Yolu
Başvurulan SDK dosyasının yolunu görüntüler.

### <a name="uri"></a>Urı
Dosyayı kaynak dosya olarak eklemek için projenin HTML veya JavaScript dosyalarına dahil edilecek URI'yi görüntüler.

### <a name="version"></a>Sürüm
Başvuru sürümünü görüntüler.

## <a name="see-also"></a>Ayrıca bkz.

- [Proje ve Çözüm Özelliklerini Yönetme](../../ide/managing-project-and-solution-properties.md)