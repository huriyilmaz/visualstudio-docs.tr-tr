---
title: Konsol projelerinde hata ayıklamaya hazırlanma | Microsoft Docs
description: Konsol projelerinde (C#, C++, Visual Basic, F#) hata ayıklamaya hazırlanma hakkında bilgi Visual Studio.
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
ms.openlocfilehash: ad23e0c60d995a59fcd64e952b1b52fa4e3df5ae0199468338fdceb92595ec34
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121404518"
---
# <a name="debugging-preparation-console-projects-c-c-visual-basic-f"></a>Hata Ayıklama Hazırlığı: Konsol Projeleri (C#, C++, Visual Basic, F#)

Konsol projesinde hata ayıklamaya hazırlanmak, komut satırı bağımsız değişkenlerini ayarlama ve hata ayıklama için uygulamayı duraklatma gibi bazı ek noktalarla birlikte Windows projesinde hata ayıklamaya hazırlanmaya benzer. Daha fazla bilgi için [bkz. Form uygulamaları için Windows hazırlama.](../debugger/debugging-preparation-windows-forms-applications.md) Tüm konsol uygulamalarının benzerliği nedeniyle, bu konu aşağıdaki proje türlerini kapsar:

- C#, Visual Basic ve F# Konsol Uygulaması

- C++ Konsol Uygulaması (.NET)

- C++ Konsol Uygulaması (Win32)

  Konsol uygulaması, giriş kabul **etmek** ve çıkış iletilerini görüntülemek için Konsol penceresini kullanır. Konsol penceresine **yazmak** için, uygulamanın Hata Ayıklama nesnesi yerine **Konsol** nesnesini kullanması gerekir. Çıkış penceresine **Visual Studio için,** her zamanki gibi Hata Ayıklama nesnesini kullanın. Uygulamanın yazdığı yeri biliyor veya iletileri yanlış yerde arıyor olabileceğinizden emin olun. Daha fazla bilgi için [bkz. Konsol Sınıfı,](/dotnet/api/system.console) [Hata Ayıklama Sınıfı](/dotnet/api/system.diagnostics.debug)ve [Çıkış Penceresi.](../ide/reference/output-window.md)

## <a name="set-command-line-arguments"></a>Komut satırı bağımsız değişkenlerini ayarlama

Konsol uygulamanız için komut satırı bağımsız değişkenleri belirtmeniz gerekir. Daha fazla bilgi için [bkz. Project Ayarlar C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)Hata Ayıklama Yapılandırması, [Project Ayarlar](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)için Visual Basic Hata Ayıklama Yapılandırması veya C# Hata [Ayıklama Yapılandırmaları için Project Ayarlar.](../debugger/project-settings-for-csharp-debug-configurations.md)

Tüm proje özellikleri gibi, bu bağımsız değişkenler de hata ayıklama oturumları arasında ve Visual Studio kalıcıdır. Bu nedenle, konsol uygulaması daha önce hata ayıklamış olabileceğiniz bir uygulama ise, Özellik Sayfaları iletişim kutusuna girilen önceki oturumlardan bağımsız **\<Project> değişkenler olabileceğini** unutmayın.

## <a name="start-the-application"></a>Uygulamayı başlatma

 Bazı konsol uygulamaları başlatılıyorsa, tamamlandıktan sonra çıkışa kadar çalışırlar. Bu davranış size yürütmeyi ve hata ayıklamayı kesmeye yetecek kadar zaman vermey olabilir. Bir uygulamada hata ayıklamak için, uygulamayı başlatmak için aşağıdaki yordamlardan birini kullanın:

- Kodunda bir kesme noktası ayarlayın ve uygulamanıza başlayabilirsiniz.

- **F10** **(** Hata Ayıklama Adımı ) veya  >   **F11** ( Hata Ayıklama Adımını Içine) kullanarak uygulamanıza başlama ve ardından'a tıklamak için Çalıştır gibi diğer seçenekleri kullanarak  >   **kodda gezinme.**

- Kod düzenleyicisinde bir satıra sağ tıklayın ve İmleç için **çalıştır'ı seçin.**

  Bir konsol uygulamasında hata ayıklarken, uygulamayı bir konsol uygulamasından değil komut isteminden Visual Studio. Bu durumda, uygulamayı komut isteminden başlatabilirsiniz ve hata ayıklayıcısını Visual Studio iliştirebilirsiniz. Daha fazla bilgi için [bkz. Çalışan İşlemlere Ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

  Bir konsol uygulamasını bir konsol Visual Studio, **bazen** konsol penceresinin arkasında Visual Studio görünür. Konsol uygulamanızı Visual Studio başlatmaya çalışırsanız ve hiçbir şey olmuyor gibi görünüyorsa, Visual Studio deneyin.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerel Kodda Hata Ayıklama](../debugger/debugging-native-code.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C++ projelerinde hata ayıklamaya hazırlanma](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project Ayarlar C++ Hata Ayıklama Yapılandırması için yapılandırma](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Hata Ayıklayıcı Güvenliği](../debugger/debugger-security.md)