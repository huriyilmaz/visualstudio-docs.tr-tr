---
title: Visual Studio komut tablosu (. Vsct) dosyaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cde3b86e19788c41df6e8f1c79a6bf829f491170
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675255"
---
# <a name="visual-studio-command-table-vsct-files"></a>Visual Studio Komut Tablosu (.Vsct) Dosyaları
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Komut tablosu yapılandırma dosyası, VSPackage 'un içerdiği komut kümesini açıklayan bir metin dosyasıdır. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]Komut tablosu (vsct) derleyicisi, XML tabanlı yapılandırma dosyalarını (. vsct dosyaları) ikili komut tablosu çıktısı (. CTO) dosyalarına derler. Sonuç. CTO dosyaları,. ctc yapılandırma dosyalarını derlemek için komut tablosu (CTC) derleyicisi kullanılarak oluşturulmuş olanlarla aynıdır. Ancak, XML tabanlı. vsct dosyaları, XML Düzenleyicisi ve XML IntelliSense gibi bazı avantajlara sahiptir.  
  
 . Vsct dosyalarının sözdizimi ve semantiği hakkında daha fazla bilgi edinmek için bkz. [XML komut tablosu tasarlama (. Vsct) dosyaları](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [XML Komut Tablosu (.Vsct) Dosyaları Tasarlama](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 . Vsct dosyalarının nasıl tasarlanacağını açıklar.  
  
 [Nasıl Yapılır: .Vsct Dosyası Oluşturma](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 . Vsct dosyası oluşturma yöntemlerini karşılaştırır. Yeni bir. vsct dosyasını el ile oluşturma işlemini açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [VSCT XML Şeması Başvurusu](../../extensibility/vsct-xml-schema-reference.md)  
 Komut tablosu XML yapılandırma dosyasının her bölümü hakkındaki ayrıntıları sağlar.  
  
 [Komut tablosu yapılandırması (. CTC) dosyaları](https://msdn.microsoft.com/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Kullanım dışı. CTC dosya biçimine bir genel bakış sunar.  
  
 [VSPackage’ların Kullanıcı Arabirimi Öğeleri Eklemesi](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Komut tablosu biçim belirtimini açıklar.  
  
 [VSPackage’lardaki Kaynaklar](../../extensibility/internals/resources-in-vspackages.md)  
 Yönetilen VSPackages 'te yönetilen ve yönetilmeyen kaynakların nasıl kullanılacağını açıklar.  
  
 [Komutlar, Menüler ve Araç Çubukları](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Menüler, araç çubukları ve komut açılan kutuları içeren bir kullanıcı arabirimi oluşturmayı açıklar.
