---
title: Hata Ayıklama Sayfası, Proje Tasarımcısı
ms.date: 06/27/2018
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vb.ProjectPropertiesDebug
helpviewer_keywords:
- Project Designer, Debug page
- Debug page in Project Designer
ms.assetid: ef11eae9-df96-4e20-aabd-2678ba317140
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 16be10dc69f203e52eb0dccc0e0738399d37ee3d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649428"
---
# <a name="debug-page-project-designer"></a>Hata Ayıklama Sayfası, Proje Tasarımcısı

Visual Basic veya C# projesinde hata ayıklama davranışı için özellikleri ayarlamak için **Proje Tasarımcısı'nın** **Hata Ayıklama** sayfasını kullanın.

**Hata Ayıklama** sayfasına erişmek için **Çözüm Gezgini'nde**bir proje düğümü seçin. **Proje** menüsünde ** \<ProjectName> Properties'i**seçin. Proje **Tasarımcısı** göründüğünde **Hata Ayıklama** sekmesini tıklatın.

> [!NOTE]
> Bu konu UWP uygulamaları için geçerli değildir. UWP uygulamaları için [hata ayıklama oturumu (VB, C#, C++ ve XAML) başlat'a](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) bakın.

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki seçenekler, görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmenize olanak sağlar.

**Yapılandırma**

Hangi yapılandırma ayarlarının görüntülenecin veya değiştirilen leri belirtir. Ayarlar Hata **Ayıklama** (varsayılan), **Sürüm**veya **Tüm Yapılandırmalar**olabilir.

**Platform**

Hangi platform ayarlarının görüntüleneceğin veya değiştirilen leri belirtir. Seçenekler herhangi **bir CPU** (varsayılan), **x64**ve **x86**içerebilir.

## <a name="start-action"></a>Eylemi başlatma

**Başlangıç eylemi,** uygulama hata ayıklandığında başlayacak öğeyi gösterir: proje, özel bir program, bir URL veya hiçbir şey. Varsayılan olarak, bu seçenek **projeyi başlatacak**şekilde ayarlanır. **Hata Ayıklama** sayfasındaki **Eylem Başlat** ayarı `StartAction` özelliğin değerini belirler.

**Projeyi başlat**

Uygulama debugged olduğunda yürütülebilir (Windows Application ve Console Application projeleri için) başlatılması gerektiğini belirtmek için bu seçeneği belirleyin. Bu seçenek varsayılan olarak seçilidir.

**Harici programı başlatın**

Uygulama debugged olduğunda belirli bir programın başlatılması gerektiğini belirtmek için bu seçeneği belirleyin.

**URL ile tarayıcıyı başlatın**

Uygulama debugged olduğunda belirli bir URL erişilebilir olması gerektiğini belirtmek için bu seçeneği belirleyin.

## <a name="start-options"></a>Başlangıç seçenekleri

**Komut satırı bağımsız değişkenleri**

Bu metin kutusuna, hata ayıklama için kullanılacak komut satırı bağımsız değişkenlerini girin.

**Çalışma dizini**

Bu metin kutusuna, projenin başlatılan dizini girin. Veya bir dizin seçmek için Gözat düğmesine (**...**) tıklayın.

**Uzak makineyi kullanma**

Uygulamayı uzak bir bilgisayardan hata ayıklamak için bu onay kutusunu seçin ve metin kutusundaki uzak bilgisayara giden yolu girin.

## <a name="debugger-engines"></a>Hata ayıklama motorları

**Yerel kod hata ayıklama etkinleştirme**

Bu seçenek, yerel kodun hata ayıklamanın desteklenip desteklenmediğini belirtir. COM nesnelerine arama yapıyorsanız veya projenizi çağıran yerel kodla yazılmış özel bir program başlatıyorsanız ve yerel kodu ayıklamanız gerekiyorsa, bu onay kutusunu seçin. Yönetilmeyen kodun hata ayıklamadevre dışı devre dışı kalmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak temizlenir.

**SQL Server hata ayıklama etkinleştirme**

Visual Basic uygulamanızdan SQL yordamlarının hata ayıklanmasını etkinleştirmek veya devre dışı kakmak için bu onay kutusunu seçin veya temizleyin. Bu onay kutusu varsayılan olarak temizlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
- [C# Hata Ayıklama Yapılandırmaları için Proje Ayarları](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Görsel Temel Hata Ayıklama Yapılandırması için Proje Ayarları](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Güvenli ClickOnce uygulamaları](../../deployment/securing-clickonce-applications.md)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)
