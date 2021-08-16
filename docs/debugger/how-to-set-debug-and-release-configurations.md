---
title: Hata ayıklama ve yayın yapılandırmalarını | Microsoft Docs
description: Hata ayıklama ve yayın yapılandırmalarını Visual Studio. Hata ayıklama için hata ayıklama sürümünü ve son sürüm dağıtımının yayın sürümünü derlemenizi sağlar.
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
ms.openlocfilehash: 77b79a2ffdb81ab6d23de32cbeefb3fcb8d7248728a17571304121c28c59c152
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121379060"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Hata ayıklama ve yayın yapılandırmalarını Visual Studio

Visual Studio projelerinin programınız için ayrı sürüm ve hata ayıklama yapılandırmaları vardır. Hata ayıklama için hata ayıklama sürümünü ve son sürüm dağıtımının yayın sürümünü derlemenizi sağlar.

Hata ayıklama yapılandırmasında, programınız tam sembolik hata ayıklama bilgileriyle derlenmiş ve iyileştirmesi yoktur. Kaynak kod ve oluşturulan yönergeler arasındaki ilişki daha karmaşık olduğundan, iyileştirme hata ayıklamayı karmaşık hale gelir.

Programınız yayın yapılandırması sembolik hata ayıklama bilgilerine sahip değil ve tamamen iyileştirilmiş. Yönetilen kod ve C++ kodu için, kullanılan derleyici seçeneklerine bağlı olarak hata ayıklama bilgileri .pdb [dosyalarında](#BKMK_symbols_release) oluşturulabilir. .pdb dosyaları oluşturmak, daha sonra yayın sürümünüzde hata ayıklamanız gerekirse yararlı olabilir.

Derleme yapılandırmaları hakkında daha fazla bilgi için [bkz. Derleme yapılandırmalarını anlama.](../ide/understanding-build-configurations.md)

Derleme yapılandırmasını Derleme menüsünden, **araç** çubuğundan veya projenin özellik sayfalarından değiştirebilirsiniz. Project sayfaları dile özgü olabilir. Aşağıdaki yordamda, menüden ve araç çubuğundan derleme yapılandırmasını değiştirme işlemi gösterilmiştir. Farklı dillerdeki projelerde derleme yapılandırmasını değiştirme hakkında daha fazla bilgi için aşağıdaki [Ayrıca bkz.](#see-also) bölümüne bakın.

## <a name="change-the-build-configuration"></a>Derleme yapılandırmasını değiştirme

Derleme yapılandırmasını değiştirmek için:

* Derleme **menüsünden** Hata **Ayıkla'Yapılandırma Yöneticisi'ı** ve ardından Hata **Ayıkla veya Serbest Bırak'ı** **seçin.**

veya

* Araç çubuğunda Çözüm Yapılandırmaları **listesinden Hata** **Ayıkla veya** **Serbest Bırak'ı** seçin.

  ![araç çubukları derleme yapılandırması](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Derleme için sembol (.pdb) dosyaları oluşturma (C#, C++, Visual Basic, F#)

Sembol (.pdb) dosyaları ve dahil etmek istediğiniz hata ayıklama bilgilerini seçebilirsiniz. Çoğu proje türü için, derleyici hata ayıklama ve yayın derlemeleri için varsayılan olarak sembol dosyaları üretirken, diğer varsayılan ayarlar proje türüne ve sürüme Visual Studio farklılık gösterir.

> [!IMPORTANT]
> Hata ayıklayıcı, yalnızca yürütülebilir dosya oluşturulduğunda, oluşturulan .pdb dosyasıyla tam olarak eşleşen bir yürütülebilir dosya için bir .pdb dosyasını yükler (yani, .pdb özgün olmalı veya özgün .pdb'nin kopyasını olmalıdır). Daha fazla bilgi için bkz. Visual Studio hata ayıklayıcısı sembol dosyalarının, ile derlenilen ikili dosyalarla tam [olarak eşleşmesi için](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)neden gerekli? .

Her proje türünün bu seçenekleri ayarlamanın farklı bir yolu olabilir.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>C#, ASP.NET veya Visual Basic oluşturma

C# veya Visual Basic'de hata ayıklama yapılandırmaları için proje ayarları hakkında ayrıntılı bilgi için bkz. [C#](../debugger/project-settings-for-csharp-debug-configurations.md) hata ayıklama yapılandırması için Project ayarları veya bir hata ayıklama yapılandırması için Project ayarları [Visual Basic ayarları.](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)

1. Bu Çözüm Gezgini projesini seçin.

2. Özellikler simgesini **seçin** (veya **Alt+Enter tuşlarına basın).**

3. Yan bölmede Derle (veya **Derle'yi** **Visual Basic).**

4. Yapılandırma listesinde **Hata** Ayıkla veya **Serbest Bırak'ı** **seçin.**

5. Gelişmiş düğmesini **(veya** gelişmiş derleme **seçenekleri düğmesini)** Visual Basic.

6. Hata ayıklama **bilgileri listesinde (veya** Hata ayıklama bilgileri oluştur listesinde Visual Basic **Tam,** **Yalnızca Pdb veya** Taşınabilir'i **seçin.** 

   Taşınabilir biçim, .NET Core için en son platformlar arası biçimdir. Seçenekler hakkında daha fazla bilgi için [bkz. Gelişmiş Derleme Ayarlar iletişim kutusu (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![C'de derlemeler için PDB oluşturma #](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Projenizi yapılandırın.

   Derleyici, sembol dosyalarını yürütülebilir dosyayla veya ana çıkış dosyasıyla aynı klasörde oluşturur.

### <a name="generate-symbol-files-for-a-c-project"></a>C++ projesi için sembol dosyaları oluşturma

1. Bu Çözüm Gezgini projesini seçin.

2. Özellikler simgesini **seçin** (veya **Alt+Enter tuşlarına basın).**

3. Yapılandırma listesinde **Hata** Ayıkla veya **Serbest Bırak'ı** **seçin.**

4. Yan bölmede, Hata Ayıklama **için >'ı** ve ardından Hata Ayıklama Bilgisi Oluştur **seçeneklerini belirleyin.**

   C++ içinde hata ayıklama yapılandırmaları için proje ayarları hakkında ayrıntılı bilgi için [bkz. Project C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)hata ayıklama yapılandırması için yapılandırma ayarları.

5. Program Veritabanı Dosyaları **Oluştur seçeneklerini yapılandırma.**

   Çoğu C++ projesinde varsayılan değer, çıktı `$(OutDir)$(TargetName).pdb` klasöründe .pdb dosyaları oluşturan değeridir.

   ![C++ içinde derlemeler için PDB oluşturma](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Projenizi yapılandırın.

   Derleyici, sembol dosyalarını yürütülebilir dosyayla veya ana çıkış dosyasıyla aynı klasörde oluşturur.

## <a name="see-also"></a><a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcısında sembol (.pdb) dosyalarını ve Visual Studio belirtin](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)<br/>
- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Project C# hata ayıklama yapılandırması için ayarları değiştirme](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Nasıl kullanılır: Yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md)