---
title: 'Nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.builds
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
caps.latest.revision: 48
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4984355c12a92529a943fe6778740ac2d7f522f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703658"
---
# <a name="how-to-set-debug-and-release-configurations"></a>Nasıl Yapılır: Hata Ayıklama ve Dağıtım Yapılandırmalarını Ayarlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio projeleri, programınız için ayrı sürüm ve hata ayıklama yapılandırmalarına sahiptir. Adların de gösterildiği gibi, hata ayıklama için hata ayıklama sürümü ve son sürüm dağıtımı için yayın sürümü oluşturacaksınız.  
  
 Programınızın hata ayıklama yapılandırması, tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirme yapılmaz. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır.  
  
 Programınızın yayın yapılandırması sembolik hata ayıklama bilgisi içermez ve tamamen iyileştirilir. Hata ayıklama bilgileri, kullanılan derleyici seçeneklerine bağlı olarak PDB dosyalarında oluşturulabilir. Daha sonra yayın sürümünüzde hata ayıklaması yapmanız gerekiyorsa PDB dosyalarının oluşturulması çok yararlı olabilir.  
  
 Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).  
  
 Yapı yapılandırmasını, araç çubuğundan veya projenin özellik sayfalarında **Yapı** menüsünden değiştirebilirsiniz. Proje özellik sayfaları dile özgüdür. Aşağıdaki yordamda, yapı yapılandırmasının menü ve araç çubuğundan nasıl değiştirileceği gösterilmektedir. Farklı dillerdeki projelerde yapı yapılandırmasını değiştirme hakkında daha fazla bilgi için aşağıdaki Ilgili konular bölümüne bakın.  
  
### <a name="to-change-the-build-configuration"></a>Yapı yapılandırmasını değiştirmek için  
  
1. Derleme menüsünden: **Oluştur/Configuration Manager**' a tıklayın, ardından **Hata Ayıkla** veya **Yayınla**' yı seçin.  
  
2. Araç çubuğunda, **çözüm yapılandırması** liste kutusunda **Hata Ayıkla** veya **Yayınla** ' yı seçin.  
  
     ![araç çubuğu derleme yapılandırması](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")  
  
     Bu araç çubuğu Express sürümlerinde kullanılamaz. Yapılandırmayı seçmek için **Build Solution komutunu F6** ve **hata ayıklamayı Başlat F5** menü öğelerini kullanabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)   
 [Hata ayıklama ve yayın projesi yapılandırması](https://msdn.microsoft.com/0440b300-0614-4511-901a-105b771b236e)
