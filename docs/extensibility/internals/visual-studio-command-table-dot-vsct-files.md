---
title: Visual Studio komut tablosu (. Vsct) dosyaları | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 24ebac7aee2294d2ad8cee06cd88102bb8d3fd78
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012353"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio Komut Tablosu (.Vsct) Dosyaları
Komut tablosu yapılandırma dosyası, VSPackage 'un içerdiği komut kümesini açıklayan bir metin dosyasıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Komut tablosu (vsct) derleyicisi, XML tabanlı yapılandırma dosyalarını (. vsct dosyaları) ikili komut tablosu çıktısı (. CTO) dosyalarına derler. Sonuç. CTO dosyaları,. ctc yapılandırma dosyalarını derlemek için komut tablosu (CTC) derleyicisi kullanılarak oluşturulmuş olanlarla aynıdır. Ancak, XML tabanlı. vsct dosyaları, XML Düzenleyicisi ve XML IntelliSense gibi bazı avantajlara sahiptir.

 . Vsct dosyalarının sözdizimi ve semantiği hakkında daha fazla bilgi edinmek için bkz. [XML komut tablosu tasarlama (. Vsct) dosyaları](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Bu Bölümde
 [XML Komut Tablosu (.Vsct) Dosyaları Tasarlama](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 . Vsct dosyalarının nasıl tasarlanacağını açıklar.

 [Nasıl Yapılır: .Vsct Dosyası Oluşturma](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 . Vsct dosyası oluşturma yöntemlerini karşılaştırır. Yeni bir. vsct dosyasını el ile oluşturma işlemini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)

 Komut tablosu XML yapılandırma dosyasının her bölümü hakkındaki ayrıntıları sağlar.

 [Komut tablosu yapılandırması (. CTC) dosyaları](/previous-versions/bb165153(v=vs.100)) , kullanım dışı. CTC dosya biçimine bir genel bakış sunar.

 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut tablosu biçim belirtimini açıklar.

 [VSPackage’lardaki Kaynaklar](../../extensibility/internals/resources-in-vspackages.md)

 Yönetilen VSPackages 'te yönetilen ve yönetilmeyen kaynakların nasıl kullanılacağını açıklar.

 [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)

 Menüler, araç çubukları ve komut açılan kutuları içeren bir kullanıcı arabirimi oluşturmayı açıklar.