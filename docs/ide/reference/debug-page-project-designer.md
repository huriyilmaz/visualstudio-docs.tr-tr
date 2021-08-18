---
title: Hata Ayıklama Sayfası, Proje Tasarımcısı
description: Project Designer'ın Hata Ayıklama sayfasını kullanarak bir Visual Basic veya C# projesinde hata ayıklama özelliklerini ayarlayın. Ayarların açıklamaları için bu makaleye bakın.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 5a79f12eda3d166b2154e71faefcc60e2457049ada19b5b3cd0d558e6c40e012
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429517"
---
# <a name="debug-page-project-designer"></a>Hata Ayıklama Sayfası, Proje Tasarımcısı

Project  **Tasarımcısı'nın** Hata Ayıklama sayfasını kullanarak bir Visual Basic veya C# projesinde hata ayıklama davranışının özelliklerini ayarlayın.

Hata Ayıklama sayfasına **erişmek** için, **Çözüm Gezgini.** Yeni **Project** Özellikler'i **\<ProjectName> seçin.** Project **Tasarımcısı göründüğünde** Hata Ayıkla **sekmesine** tıklayın.

> [!NOTE]
> Bu konu UWP uygulamaları için geçerli değildir. UWP uygulamaları için bkz. Hata ayıklama oturumu [başlatma (VB, C#, C++ ve XAML).](../../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)

## <a name="configuration-and-platform"></a>Yapılandırma ve Platform

Aşağıdaki seçenekler, görüntülemek veya değiştirmek için yapılandırmayı ve platformu seçmenize olanak sağlar.

**Yapılandırma**

Hangi yapılandırma ayarlarının görüntü veya değiştirmesi gerektir olduğunu belirtir. Ayarlar Hata Ayıklama **(varsayılan),** Sürüm **veya Tüm** **Yapılandırmalar olabilir.**

**Platform**

Hangi platform ayarlarının görüntü veya değiştirmesi gerektir olduğunu belirtir. Seçenekler Herhangi bir **CPU (varsayılan),** **x64** ve **x86 olabilir.**

## <a name="start-action"></a>Başlatma eylemi

**Başlatma eylemi,** uygulama hata ayıklarken başlatacak öğeyi gösterir: proje, özel program, URL veya hiçbir şey. Varsayılan olarak, bu seçenek Projeyi başlat **olarak ayarlanır.** Hata **Ayıklama** sayfasındaki **Eylemi Başlat** ayarı özelliğin değerini `StartAction` belirler.

**Projeyi başlatma**

Uygulama hata ayıklaması sırasında yürütülebilir dosyanın (Windows Uygulama ve Konsol Uygulaması projeleri için) başlat gerektiğini belirtmek için bu seçeneği belirleyin. Bu seçenek varsayılan olarak seçilidir.

**Dış programı başlatma**

Uygulama hata ayıklarken belirli bir programın başlat gerektiğini belirtmek için bu seçeneği belirleyin.

**URL ile tarayıcıyı başlatma**

Uygulamanın hata ayıklaması sırasında belirli bir URL'ye erişilemediklerini belirtmek için bu seçeneği belirleyin.

## <a name="start-options"></a>Başlatma seçenekleri

**Komut satırı bağımsız değişkenleri**

Bu metin kutusuna hata ayıklama için kullanmak üzere komut satırı bağımsız değişkenlerini girin.

**Çalışma dizini**

Bu metin kutusuna, projenin hangi dizinden başlat olacağını girin. Veya bir dizin seçmek için Gözat düğmesine (**...**) tıklayın.

**Uzak makineyi kullanma**

Uygulamanın hata ayıklaması için uzak bir bilgisayardan bu onay kutusunu seçin ve metin kutusuna uzak bilgisayarın yolunu girin.

## <a name="debugger-engines"></a>Hata ayıklayıcı altyapıları

**Yerel kodda hata ayıklamayı etkinleştirme**

Bu seçenek, yerel kodda hata ayıklamanın destek olup olmadığını belirtir. COM nesnelerine çağrı yapıyorsanız veya projenizi çağıran yerel kodla yazılmış özel bir program başlatabilir ve yerel kodda hata ayıklamanız gerekirse bu onay kutusunu işaretleyin. Bu onay kutusunu temizerek, unmanaged kodda hata ayıklamayı devre dışı bırakma. Bu onay kutusu varsayılan olarak temizdir.

**Hata SQL Server etkinleştirme**

Uygulama uygulamanıza ilişkin yordamlarda hata ayıklamayı etkinleştirmek veya devre dışı bırakmak SQL onay kutusunu Visual Basic temizleyin. Bu onay kutusu varsayılan olarak temizdir.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
- [Project Ayarlar C# Hata Ayıklama Yapılandırmaları için Yapılandırmalar](../../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project Ayarlar Hata Ayıklama Visual Basic için yapılandırma](../../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Uygulama ClickOnce güvenliğini sağlama](../../deployment/securing-clickonce-applications.md)
- [Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme](../../ide/how-to-create-and-edit-configurations.md)
