---
title: Konsol projelerinde hata ayıklama hazırlığı | Microsoft Docs
description: 'Visual Studio içindeki konsol projelerinde hata ayıklama hazırlığı (C#, C++, Visual Basic, F #) hakkında bilgi alın.'
ms.custom: SEO-VS-2020
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e627e88eb1dbfefe710233eb0136bbe650c782e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122097421"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>hata ayıklama hazırlığı: konsol projeleri (C#, C++, Visual Basic, F #)

konsol projesinde hata ayıklamaya hazırlanma, komut satırı bağımsız değişkenlerini ayarlama ve uygulamanın hata ayıklama için nasıl duraklatılacağı gibi bazı ek hususlar içeren bir Windows projesinde hata ayıklamaya hazırlanmaya benzer. daha fazla bilgi için bkz. [Windows Form uygulamaları için hata ayıklama hazırlığı](../debugger/debugging-preparation-windows-forms-applications.md). Tüm konsol uygulamalarının benzerliği nedeniyle, bu konu aşağıdaki proje türlerini içerir:

- C#, Visual Basic ve F # konsol uygulaması

- C++ konsol uygulaması (.NET)

- C++ konsol uygulaması (Win32)

  Konsol uygulaması girişi kabul etmek ve çıkış iletilerini göstermek için **konsol** penceresini kullanır. **Konsol** penceresine yazmak Için uygulamanızın hata ayıklama nesnesi yerine **konsol** nesnesini kullanması gerekir. **Visual Studio çıkış** penceresine yazmak için, her zamanki gibi hata ayıklama nesnesini kullanın. Uygulamanızın nerede yazıldığını öğrendiğinizden emin olun veya yanlış yerde iletileri arıyor olabilirsiniz. Daha fazla bilgi için bkz. [konsol sınıfı](/dotnet/api/system.console), [hata ayıklama sınıfı](/dotnet/api/system.diagnostics.debug)ve [Çıkış penceresi](../ide/reference/output-window.md).

## <a name="set-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini ayarla

Konsol uygulamanız için komut satırı bağımsız değişkenlerini belirtmeniz gerekebilir. daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması için Project Ayarlar](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic hata ayıklama yapılandırması Ayarlar Project](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)veya [C# hata ayıklama yapılandırmaları için Project](../debugger/project-settings-for-csharp-debug-configurations.md)Ayarlar.

tüm proje özellikleri gibi, bu bağımsız değişkenler hata ayıklama oturumları arasında ve Visual Studio oturumları arasında kalır. Bu nedenle, konsol uygulaması daha önce hata ayıkladıysanız, **\<Project> Özellik sayfaları** iletişim kutusuna girilen önceki oturumlardan bağımsız değişkenlerin olabileceğini unutmayın.

## <a name="start-the-application"></a>Uygulamayı başlatma

 Bazı konsol uygulamaları başlatıldığında, tamamlanmaları ve sonra çıkmak üzere çalışır. Bu davranış, yürütme ve hata ayıklama işlemlerini kesmeniz için yeterli zaman sunmayabilir. Bir uygulamada hata ayıklayabilmek için, uygulamayı başlatmak için aşağıdaki yordamlardan birini kullanın:

- Kodunuzda bir kesme noktası ayarlayın ve uygulamanızı başlatın.

- Uygulamanızı **F10** (**hata ayıklama**  >  **adımı**) veya **F11** (**hata ayıklama**  >  **adımı**) kullanarak başlatın ve ardından **Çalıştır** gibi diğer seçenekleri kullanarak kod üzerinden ilerleyin.

- Kod Düzenleyicisi 'nde bir satıra sağ tıklayın ve **imlece Çalıştır**' ı seçin.

  Bir konsol uygulamasında hata ayıklarken, uygulamayı Visual Studio yerine komut isteminden başlatmak isteyebilirsiniz. bu durumda, uygulamayı komut isteminden başlatabilir ve Visual Studio hata ayıklayıcıyı buna iliştirebilirsiniz. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

  Visual Studio bir konsol uygulaması başlattığınızda, **konsol** penceresi bazen Visual Studio penceresinin arkasında görünür. konsol uygulamanızı Visual Studio başlatmaya çalışırsanız ve hiçbir şey gerçekleşmezse, Visual Studio penceresini taşımayı deneyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [C++ hata ayıklama yapılandırması için Project Ayarlar](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)