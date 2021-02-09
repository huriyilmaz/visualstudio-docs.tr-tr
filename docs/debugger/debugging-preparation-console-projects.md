---
title: Konsol projelerinde hata ayıklama hazırlığı | Microsoft Docs
description: "Visual Studio 'da konsol projelerinde hata ayıklama hazırlığı (C#, C++, Visual Basic, F #) hakkında bilgi alın."
ms.custom: SEO-VS-2020, seodec18
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e39cb7df53a12b97d297ee739338c42a3201089f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99872527"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Hata Ayıklama Hazırlığı: Konsol projeleri (C#, C++, Visual Basic, F #)

Konsol projesinde hata ayıklamaya hazırlanma, komut satırı bağımsız değişkenlerini ayarlama ve uygulamanın hata ayıklama için nasıl duraklatılacağı gibi bazı ek hususlar içeren bir Windows projesinde hata ayıklamaya hazırlanmaya benzer. Daha fazla bilgi için bkz. [Windows Forms uygulamalar](../debugger/debugging-preparation-windows-forms-applications.md)ve [hata ayıklama hazırlığı: Windows Forms uygulamalar (.net)](/previous-versions/visualstudio/visual-studio-2010/sez9z95a(v=vs.100)). Tüm konsol uygulamalarının benzerliği nedeniyle, bu konu aşağıdaki proje türlerini içerir:

- C#, Visual Basic ve F # konsol uygulaması

- C++ konsol uygulaması (.NET)

- C++ konsol uygulaması (Win32)

  Konsol uygulaması girişi kabul etmek ve çıkış iletilerini göstermek için **konsol** penceresini kullanır. **Konsol** penceresine yazmak Için uygulamanızın hata ayıklama nesnesi yerine **konsol** nesnesini kullanması gerekir. **Visual Studio çıktı** penceresine yazmak Için, hata ayıklama nesnesini her zamanki gibi kullanın. Uygulamanızın nerede yazıldığını öğrendiğinizden emin olun veya yanlış yerde iletileri arıyor olabilirsiniz. Daha fazla bilgi için bkz. [konsol sınıfı](/dotnet/api/system.console), [hata ayıklama sınıfı](/dotnet/api/system.diagnostics.debug)ve [Çıkış penceresi](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini ayarla

Konsol uygulamanız için komut satırı bağımsız değişkenlerini belirtmeniz gerekebilir. Daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması Için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic hata ayıklama yapılandırması için proje](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ayarları veya [C# hata ayıklama yapılandırmaları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md).

Tüm proje özellikleri gibi, bu bağımsız değişkenler hata ayıklama oturumları arasında ve Visual Studio oturumları arasında kalır. Bu nedenle, konsol uygulaması daha önce hata ayıkladıysanız, **\<Project> Özellik sayfaları** iletişim kutusuna girilen önceki oturumlardan bağımsız değişkenlerin olabileceğini unutmayın.

## <a name="start-the-application"></a>Uygulamayı başlatma

 Bazı konsol uygulamaları başlatıldığında, tamamlanmaları ve sonra çıkmak üzere çalışır. Bu davranış, yürütme ve hata ayıklama işlemlerini kesmeniz için yeterli zaman sunmayabilir. Bir uygulamada hata ayıklayabilmek için, uygulamayı başlatmak için aşağıdaki yordamlardan birini kullanın:

- Kodunuzda bir kesme noktası ayarlayın ve uygulamanızı başlatın.

- Uygulamanızı **F10** (**hata ayıklama**  >  **adımı**) veya **F11** (**hata ayıklama**  >  **adımı**) kullanarak başlatın ve ardından **Çalıştır** gibi diğer seçenekleri kullanarak kod üzerinden ilerleyin.

- Kod Düzenleyicisi 'nde bir satıra sağ tıklayın ve **imlece Çalıştır**' ı seçin.

  Bir konsol uygulamasında hata ayıklarken, uygulamayı Visual Studio 'dan değil komut isteminden başlatmak isteyebilirsiniz. Bu durumda, uygulamayı komut isteminden başlatabilir ve Visual Studio hata ayıklayıcısını buna iliştirebilirsiniz. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Visual Studio 'dan bir konsol uygulaması başlattığınızda, **konsol** penceresi bazen Visual Studio penceresinin arkasında görünür. Konsol uygulamanızı Visual Studio 'dan başlatmaya çalışırsanız ve hiçbir şey gerçekleşmezse, Visual Studio penceresini taşımayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)