---
title: Konsol projelerinde hata ayıklama hazırlığı | Microsoft Docs
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
ms.openlocfilehash: ddfc17d4f9bcb1f4f2585aa91319f06be6936e6f
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431462"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Hata Ayıklama Hazırlığı: Konsol projeleriC#( C++,, Visual Basic F#,)

Konsol projesinde hata ayıklamaya hazırlanma, komut satırı bağımsız değişkenlerini ayarlama ve uygulamanın hata ayıklama için nasıl duraklatılacağı gibi bazı ek hususlar içeren bir Windows projesinde hata ayıklamaya hazırlanmaya benzer. Daha fazla bilgi için bkz. [Windows Forms uygulamalar](../debugger/debugging-preparation-windows-forms-applications.md)ve [hata ayıklama hazırlığı: Windows Forms uygulamalar (.net)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Tüm konsol uygulamalarının benzerliği nedeniyle, bu konu aşağıdaki proje türlerini içerir:

- C#, Visual Basic ve F# konsol uygulaması

- C++Konsol uygulaması (.NET)

- C++Konsol uygulaması (Win32)

  Konsol uygulaması girişi kabul etmek ve çıkış iletilerini göstermek için **konsol** penceresini kullanır. **Konsol** penceresine yazmak Için uygulamanızın hata ayıklama nesnesi yerine **konsol** nesnesini kullanması gerekir. **Visual Studio çıktı** penceresine yazmak Için, hata ayıklama nesnesini her zamanki gibi kullanın. Uygulamanızın nerede yazıldığını öğrendiğinizden emin olun veya yanlış yerde iletileri arıyor olabilirsiniz. Daha fazla bilgi için bkz. [konsol sınıfı](/dotnet/api/system.console), [hata ayıklama sınıfı](/dotnet/api/system.diagnostics.debug)ve [Çıkış penceresi](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini ayarla

Konsol uygulamanız için komut satırı bağımsız değişkenlerini belirtmeniz gerekebilir. Daha fazla bilgi için bkz. hata ayıklama [yapılandırması C++ için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic hata ayıklama yapılandırması için proje](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ayarları veya [hata ayıklama yapılandırmaları C# için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md).

Tüm proje özellikleri gibi, bu bağımsız değişkenler hata ayıklama oturumları arasında ve Visual Studio oturumları arasında kalır. Bu nedenle, konsol uygulaması daha önce hata ayıkladıysanız, **\<Proje > Özellik sayfaları** iletişim kutusuna girilen önceki oturumlardan bağımsız değişkenlerin olabileceğini unutmayın.

## <a name="start-the-application"></a>Uygulamayı başlatma

 Bazı konsol uygulamaları başlatıldığında, tamamlanmaları ve sonra çıkmak üzere çalışır. Bu davranış, yürütme ve hata ayıklama işlemlerini kesmeniz için yeterli zaman sunmayabilir. Bir uygulamada hata ayıklayabilmek için, uygulamayı başlatmak için aşağıdaki yordamlardan birini kullanın:

- Kodunuzda bir kesme noktası ayarlayın ve uygulamanızı başlatın.

- Uygulamanızı **F10** (**hata ayıklama** > **adımla**) veya **F11** (**hata ayıklama** > **adımla**) kullanarak başlatın ve ardından **Çalıştır**gibi diğer seçenekleri kullanarak kod üzerinden ilerleyin.

- Kod Düzenleyicisi 'nde bir satıra sağ tıklayın ve **imlece Çalıştır**' ı seçin.

  Bir konsol uygulamasında hata ayıklarken, uygulamayı Visual Studio 'dan değil komut isteminden başlatmak isteyebilirsiniz. Bu durumda, uygulamayı komut isteminden başlatabilir ve Visual Studio hata ayıklayıcısını buna iliştirebilirsiniz. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Visual Studio 'dan bir konsol uygulaması başlattığınızda, **konsol** penceresi bazen Visual Studio penceresinin arkasında görünür. Konsol uygulamanızı Visual Studio 'dan başlatmaya çalışırsanız ve hiçbir şey gerçekleşmezse, Visual Studio penceresini taşımayı deneyin.

## <a name="see-also"></a>Ayrıca Bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [Projelerde hata ayıklama C++ hazırlığı](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)