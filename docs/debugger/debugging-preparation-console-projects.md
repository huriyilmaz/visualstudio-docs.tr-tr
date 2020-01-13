---
title: Konsol projeleri hata ayıklamak hazırlama | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e612228bf5440936c336d286962820a02d6bd071
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916283"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Hata ayıklama hazırlığı: Konsol projeleri (C#, C++, Visual Basic F#)

Konsol projesinde hata ayıklamaya hazırlanma, komut satırı bağımsız değişkenlerini ayarlama ve uygulamanın hata ayıklama için nasıl duraklatılacağı gibi bazı ek hususlar içeren bir Windows projesinde hata ayıklamaya hazırlanmaya benzer. Daha fazla bilgi için [Windows Forms uygulamaları](../debugger/debugging-preparation-windows-forms-applications.md), ve [hata ayıklama hazırlığı: Windows Forms uygulamaları (.NET)](/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Tüm konsol uygulamaları benzerlik nedeniyle, bu konu, aşağıdaki proje türlerini içerir:

- C#, Visual Basic ve F# konsol uygulaması

- C++ konsol uygulaması (.NET)

- C++ konsol uygulaması (Win32)

  Bir konsol uygulaması kullanan **konsol** giriş kabul etmek ve çıkış iletileri görüntülemek için bir pencere. Yazılacak **konsol** penceresinde, uygulamanızın kullanmalıdır **konsol** hata ayıklama nesnesi yerine nesne. Yazılacak **Visual Studio çıkış** penceresi, hata ayıklama nesnesi zamanki kullanın. Burada, uygulama yazma veya yanlış yere iletiler için arıyor olabilirsiniz bildiğinizden emin olun. Daha fazla bilgi için [konsol sınıfı](/dotnet/api/system.console), [hata ayıklama sınıfı](/dotnet/api/system.diagnostics.debug), ve [çıkış penceresine](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini ayarla

Konsol uygulamanız için komut satırı bağımsız değişkenleri belirtmeniz gerekebilir. Daha fazla bilgi için [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md), veya [C# hata ayıklama yapılandırmaları için proje ayarları ](../debugger/project-settings-for-csharp-debug-configurations.md).

Bu bağımsız değişkenler tüm proje özellikleri gibi Visual Studio oturumları arasında hata ayıklama oturumları arasında kalıcı hale getirin. Daha önce hataları ayıklanmakta bir konsol uygulaması ise, bu nedenle, girdiğiniz önceki oturumlarını bağımsız değişkenleri olabilir unutmayın  **\<Proje > özellik sayfaları** iletişim kutusu.

## <a name="start-the-application"></a>Uygulamayı başlatma

 Bazı konsol uygulamaları başlattığınızda tamamlanmak üzere çalıştırılmasını ve çıkın. Bu davranış yürütme sonu ve hata ayıklama için yeterli zaman sağlamayabilir. Bir uygulamada hata ayıklamak için uygulamayı başlatmak için aşağıdaki prosedürlerden birini kullanın:

- Kodunuzda bir kesme noktası ayarlayın ve uygulamanızı başlatın.

- Uygulama kullanmaya başlayın **F10** (**hata ayıklama** > **Step Over**) veya **F11** (**hataayıklama**  >  **İçine adımla**) ve ardından gibi diğer seçenekleri kullanarak kod gidin **Çalıştır'ı tıklatın**.

- Kod Düzenleyicisi'nde bir satıra sağ tıklayıp **imlece kadar Çalıştır**.

  Bir konsol uygulaması hata ayıklaması yaparken, komut isteminden yerine Visual Studio uygulamayı başlatmak isteyebilirsiniz. Bu durumda, uygulamayı komut isteminden başlatmak ve Visual Studio hata ayıklayıcısını ekleyebilir. Daha fazla bilgi için [çalışan işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Visual Studio'dan bir konsol uygulaması'nı başlattığınızda **konsol** penceresi bazen Visual Studio penceresinde görüntülenir. Konsol uygulamanızı Visual Studio ve hiçbir şey başlatmaya çalışırsanız görünüyor gerçekleşir, Visual Studio penceresine gitme deneyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Projelerde hata ayıklama C++ hazırlığı](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)