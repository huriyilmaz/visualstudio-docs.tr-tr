---
title: Visual Studio Komut Tablosu (. Vsct) Dosyalar | Microsoft Dokümanlar
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
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704031"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio Komut Tablosu (.Vsct) Dosyaları
Komut tablosu yapılandırma dosyası, VSPackage'ın içerdiği komut kümesini açıklayan bir metin dosyasıdır. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Komut tablosu (VSCT) derleyicisi, XML tabanlı yapılandırma dosyalarını (.vsct dosyaları) ikili komut tablosu çıktısı (.cto) dosyalarına derler. Ortaya çıkan .cto dosyaları,.ctc yapılandırma dosyalarını derlemek için komut tablosu (CTC) derleyicisi kullanılarak oluşturulanlarla aynıdır. Ancak, XML tabanlı .vsct dosyaları, XML düzenleyicisi ve XML IntelliSense gibi bazı avantajları vardır.

 .vsct dosyalarının sözdizimi ve anlamtisi hakkında daha fazla bilgi edinmek için [Bkz. XML Komut Tablosu Tasarlama (. Vsct) Dosyaları](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Bu Bölümde
 [XML Komut Tablosu (.Vsct) Dosyaları Tasarlama](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 .vsct dosyalarının nasıl tasarlanır olduğunu açıklar.

 [Nasıl Yapılır: .Vsct Dosyası Oluşturma](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 .vsct dosyası oluşturma yöntemlerini karşılaştırır. Yeni bir .vsct dosyası oluşturma işlemini açıklar.

## <a name="related-sections"></a>İlgili Bölümler
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)

 Komut tablosu XML yapılandırma dosyasının her bölümü hakkında ayrıntılı bilgi sağlar.

 [Komut Tablosu Yapılandırması (. Ctc) Dosyalar](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) Amortismana alınan .ctc dosya biçimine genel bir bakış sunar.

 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Komut tablosu biçimi belirtimini açıklar.

 [VSPackage’lardaki Kaynaklar](../../extensibility/internals/resources-in-vspackages.md)

 Yönetilen VSPackages'te yönetilen ve yönetilmeyen kaynakların nasıl kullanılacağını açıklar.

 [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)

 Menüler, araç çubukları ve komut açılan kutularını içeren bir ara biriminin nasıl oluşturulup oluşturulabildiğini açıklar.
