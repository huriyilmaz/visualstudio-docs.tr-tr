---
title: Hata ayıklama ve yayın yapılandırmasını ayarlama | Microsoft Docs
description: Visual Studio hata ayıklama ve yayın yapılandırmasını ayarlayın. Hata ayıklama için hata ayıklama sürümü ve son sürüm dağıtımı için yayın sürümü oluşturursunuz.
ms.custom: SEO-VS-2020
ms.date: 10/05/2018
ms.topic: how-to
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 4958501cd7a6b42e6e733193b0f80bd723cdae10
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122128188"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Visual Studio hata ayıklama ve yayın yapılandırmasını ayarlama

Visual Studio projelerin, programınız için ayrı bir sürüm ve hata ayıklama yapılandırması vardır. Hata ayıklama için hata ayıklama sürümü ve son sürüm dağıtımı için yayın sürümü oluşturursunuz.

Hata ayıklama yapılandırmasında, programınız tam sembolik hata ayıklama bilgileriyle derlenir ve iyileştirme gerektirmez. Kaynak kodu ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan iyileştirme, hata ayıklamayı karmaşıklaştırır.

Programınızın yayın yapılandırmasında sembolik hata ayıklama bilgisi yoktur ve tam iyileştirilir. Yönetilen kod ve C++ kodu için, hata ayıklama bilgileri, kullanılan [derleyici seçeneklerine bağlı olarak](#BKMK_symbols_release) . pdb dosyalarında oluşturulabilir. Daha sonra yayın sürümünüzde hata ayıklaması yapmanız gerekiyorsa. pdb dosyalarının oluşturulması yararlı olabilir.

Derleme konfigürasyonları hakkında daha fazla bilgi için bkz. [derleme yapılandırmasını anlama](../ide/understanding-build-configurations.md).

Yapı yapılandırmasını, araç çubuğundan veya projenin özellik sayfalarında **Yapı** menüsünden değiştirebilirsiniz. Project özellik sayfaları dile özgüdür. Aşağıdaki yordamda, yapı yapılandırmasının menü ve araç çubuğundan nasıl değiştirileceği gösterilmektedir. Farklı dillerdeki projelerde yapı yapılandırmasını değiştirme hakkında daha fazla bilgi için aşağıdaki [Ayrıca bkz](#see-also) . bölümüne bakın.

## <a name="change-the-build-configuration"></a>Yapı yapılandırmasını değiştirme

Yapı yapılandırmasını değiştirmek için aşağıdakilerden birini yapın:

* **Derleme** menüsünden **Configuration Manager**' yi seçin ve ardından **Hata Ayıkla** veya **Yayınla**' yı seçin.

veya

* Araç çubuğunda, **çözüm yapılandırması** listesinden **Hata Ayıkla** veya **Yayınla** ' yı seçin.

  ![araç çubukları derleme yapılandırması](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>derleme (C#, C++, Visual Basic, F #) için sembol (. pdb) dosyaları oluşturma

Sembol (. pdb) dosyalarını ve dahil edilecek hata ayıklama bilgilerini oluşturmayı seçebilirsiniz. çoğu proje türü için, derleyici varsayılan olarak hata ayıklama ve yayın yapıları için sembol dosyaları üretir, diğer varsayılan ayarlar proje türü ve Visual Studio sürümüne göre farklılık gösterir.

> [!IMPORTANT]
> Hata ayıklayıcı, yalnızca yürütülebilir dosya oluşturulduğunda, oluşturulan .pdb dosyasıyla tam olarak eşleşen bir yürütülebilir dosya için bir .pdb dosyasını yükler (yani, .pdb özgün olmalı veya özgün .pdb'nin kopyasını olmalıdır). daha fazla bilgi için bkz. [neden Visual Studio hata ayıklayıcı sembol dosyalarının ile derlendikleri ikili dosyalarla tam olarak eşleşmesi gerekir?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with).

Her proje türünün bu seçenekleri ayarlamanın farklı bir yolu olabilir.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>C#, ASP.NET veya Visual Basic projesi için sembol dosyaları oluşturma

c# veya Visual Basic hata ayıklama yapılandırmalarının proje ayarları hakkında ayrıntılı bilgi için bkz. [c# hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-csharp-debug-configurations.md) veya [Visual Basic hata ayıklama yapılandırması Project ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. Çözüm Gezgini, projeyi seçin.

2. **Özellikler** simgesini seçin (veya **Alt + Enter** tuşlarına basın).

3. Yan bölmede, **Oluştur** (veya Visual Basic **Derle** ) öğesini seçin.

4. **Yapılandırma** listesinde **Hata Ayıkla** veya **Yayınla**' yı seçin.

5. **Gelişmiş** düğmesini (veya Visual Basic) **Gelişmiş derleme seçenekleri** düğmesini seçin.

6. **hata ayıklama bilgileri** listesinde (veya Visual Basic **hata ayıklama bilgileri oluştur** ' da), **tam**, **Pdb-salt** veya **taşınabilir**' ı seçin.

   Taşınabilir biçim, .NET Core için en son platformlar arası biçimdir. seçenekler hakkında daha fazla bilgi için bkz. [gelişmiş derleme Ayarlar iletişim kutusu (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![C 'de derlemeler için pdb 'leri oluşturma #](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Projenizi yapılandırın.

   Derleyici, sembol dosyalarını çalıştırılabilir veya ana çıktı dosyasıyla aynı klasörde oluşturur.

### <a name="generate-symbol-files-for-a-c-project"></a>C++ projesi için sembol dosyaları oluşturma

1. Çözüm Gezgini, projeyi seçin.

2. **Özellikler** simgesini seçin (veya **Alt + Enter** tuşlarına basın).

3. **Yapılandırma** listesinde **Hata Ayıkla** veya **Yayınla**' yı seçin.

4. Yan bölmede, **hata ayıklama > bağlayıcı**' yı seçin, ardından **hata ayıklama bilgisi oluştur** seçeneklerini belirleyin.

   c++ ' da hata ayıklama yapılandırmalarının proje ayarları hakkında ayrıntılı bilgi için bkz. [c++ hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. **Program veritabanı dosyaları oluştur** seçeneklerini yapılandırın.

   Çoğu C++ projesinde, varsayılan değer `$(OutDir)$(TargetName).pdb` . pdb dosyalarını çıkış klasöründe oluşturur.

   ![C++ ' da derlemeler için pdb 'leri oluşturma](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Projenizi yapılandırın.

   Derleyici, sembol dosyalarını çalıştırılabilir veya ana çıktı dosyasıyla aynı klasörde oluşturur.

## <a name="see-also"></a><a name="see-also"></a>Ayrıca bkz.

- [Visual Studio hata ayıklayıcısında simge (. pdb) dosyalarını ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)<br/>
- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [C# hata ayıklama yapılandırması için Project ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)