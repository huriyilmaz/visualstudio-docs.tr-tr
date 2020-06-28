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
author: Mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 406b3ecdc0e4e3f0d45c22fc9201bd37c6031152
ms.sourcegitcommit: 9e15138a34532b222e80f6b42b1a9de7b2fe0175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85418749"
---
# <a name="debug-page-project-designer"></a>Hata Ayıklama Sayfası, Proje Tasarımcısı

Visual Basic veya C# projesindeki hata ayıklama davranışının özelliklerini ayarlamak için **Proje Tasarımcısı** ' nın **hata ayıklama** sayfasını kullanın.

**Hata ayıklama** sayfasına erişmek için **Çözüm Gezgini**bir proje düğümü seçin. **Proje** menüsünde ** \<ProjectName> Özellikler**' i seçin. **Proje Tasarımcısı** göründüğünde, **Hata Ayıkla** sekmesine tıklayın.

> [!NOTE]
> Bu konu, UWP uygulamaları için geçerlidir. UWP uygulamaları için [hata ayıklama oturumu başlatma (vb, C#, C++ ve XAML)](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md) konusuna bakın.

## <a name="configuration-and-platform"></a>Yapılandırma ve platform

Aşağıdaki seçenekler, görüntülenecek veya değiştirilecek olan yapılandırmayı ve platformu seçmenizi sağlar.

**Yapılandırma**

Görüntülenecek veya değiştirilecek yapılandırma ayarlarını belirtir. Ayarlar **hata ayıklama** (varsayılan), **yayın**veya **Tüm yapılandırmalarda**olabilir.

**Platform**

Görüntülenecek veya değiştirilecek platform ayarlarını belirtir. Seçenekler **herhangi BIR CPU** (varsayılan), **x64**ve **x86**içerebilir.

## <a name="start-action"></a>Başlatma eylemi

**Başlangıç eylemi** , uygulamanın hatası ayıklandığında başlatılacak öğeyi gösterir: proje, özel program, URL veya Nothing. Varsayılan olarak, bu seçenek **Project 'ı başlatacak**şekilde ayarlanır. **Hata ayıklama** sayfasındaki **Başlangıç eylemi** ayarı özelliğin değerini belirler `StartAction` .

**Projeyi Başlat**

Uygulamanın hatası ayıklandığında yürütülebilir dosyanın (Windows uygulama ve konsol uygulaması projeleri için) başlatılıp başlatılabileceğini belirtmek için bu seçeneği belirleyin. Bu seçenek varsayılan olarak seçilidir.

**Dış programı Başlat**

Uygulamanın hatası ayıklandığında belirli bir programın başlatılmasını belirtmek için bu seçeneği belirleyin.

**Tarayıcıyı URL ile Başlat**

Uygulamanın hatası ayıklandığında belirli bir URL 'ye erişilmesi gerektiğini belirtmek için bu seçeneği belirleyin.

## <a name="start-options"></a>Başlatma seçenekleri

**Komut satırı bağımsız değişkenleri**

Bu metin kutusuna hata ayıklama için kullanılacak komut satırı bağımsız değişkenlerini girin.

**Çalışma dizini**

Bu metin kutusuna projenin başlatılacağı dizini girin. Veya bir dizin seçmek için (**...**) düğmesine tıklayın.

**Uzak makineyi kullan**

Uygulamanın uzak bir bilgisayardan hata ayıklaması yapmak için, bu onay kutusunu işaretleyin ve metin kutusuna uzak bilgisayarın yolunu girin.

## <a name="debugger-engines"></a>Hata ayıklayıcı motorları

**Yerel kod hata ayıklamasını etkinleştir**

Bu seçenek, yerel kod hata ayıklamanın desteklenip desteklenmediğini belirtir. COM nesnelerine çağrılar yapıyorsanız veya projenizi çağıran yerel kodda yazılmış özel bir program başlatırsanız ve yerel kodda hata ayıklaması yapmanız gerekiyorsa bu onay kutusunu işaretleyin. Yönetilmeyen kodun hata ayıklamasını devre dışı bırakmak için bu onay kutusunu temizleyin. Bu onay kutusu varsayılan olarak temizlenir.

**SQL Server hata ayıklamayı etkinleştir**

Visual Basic uygulamanızdan SQL yordamlarının hata ayıklamasını etkinleştirmek veya devre dışı bırakmak için bu onay kutusunu işaretleyin veya temizleyin. Bu onay kutusu varsayılan olarak temizlenir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
- [C# Hata Ayıklama Yapılandırması Proje Ayarları](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Güvenli ClickOnce uygulamaları](../../deployment/securing-clickonce-applications.md)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)
