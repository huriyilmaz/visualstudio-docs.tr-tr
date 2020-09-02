---
title: 'Hata Ayıklama Hazırlığı: Konsol projeleri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], console applications
- debugging console applications
- console applications, debugging
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5ac87f6c5ef5fcf9fc7ca5532fe7436dedb8ba97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691212"
---
# <a name="debugging-preparation-console-projects"></a>Hata Ayıklama Hazırlığı: Konsol Projeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir konsol projesinde hata ayıklamaya hazırlanma, bir Windows projesinde hata ayıklamaya hazırlanmasına benzer ve bazı ek hususlar vardır. Daha fazla bilgi için bkz. [Windows Forms uygulamalar](../debugger/debugging-preparation-windows-forms-applications.md)ve [hata ayıklama hazırlığı: Windows Forms uygulamalar (.net)](https://msdn.microsoft.com/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5). Tüm konsol uygulamalarının benzerliği nedeniyle, bu konu aşağıdaki proje türlerini içerir:  
  
- C# konsol uygulaması  
  
- Visual Basic konsol uygulaması  
  
- C++ konsol uygulaması (.NET)  
  
- C++ konsol uygulaması (Win32)  
  
  Konsol uygulamanız için komut satırı bağımsız değişkenlerini belirtmeniz gerekebilir. Daha fazla bilgi için bkz. [C++ hata ayıklama yapılandırması Için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md), [Visual Basic hata ayıklama yapılandırması için proje](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)ayarları veya [C# hata ayıklama yapılandırmaları için proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
  Tüm proje özellikleri gibi, bu bağımsız değişkenler hata ayıklama oturumları arasında ve Visual Studio oturumları arasında kalır. Bu nedenle, konsol uygulaması daha önce hata ayıkladıysanız, ** \<Project> Özellik sayfaları** iletişim kutusuna girilen önceki oturumlardan bağımsız değişkenlerin olabileceğini unutmayın.  
  
  Konsol uygulaması girişi kabul etmek ve çıkış iletilerini göstermek için **konsol** penceresini kullanır. **Konsol** penceresine yazmak Için uygulamanızın hata ayıklama nesnesi yerine **konsol** nesnesini kullanması gerekir. **Visual Studio çıktı** penceresine yazmak Için, hata ayıklama nesnesini her zamanki gibi kullanın. Uygulamanızın nerede yazıldığını öğrendiğinizden emin olun veya yanlış yerde iletileri arıyor olabilirsiniz. Daha fazla bilgi için bkz. [konsol sınıfı](https://msdn.microsoft.com/library/system.console.aspx), [hata ayıklama sınıfı](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx)ve [Çıkış penceresi](../ide/reference/output-window.md).  
  
## <a name="starting-the-application"></a>Uygulama başlatılıyor  
 Bazı konsol uygulamaları başlatıldığında, tamamlanmaları ve sonra çıkmak üzere çalışır. Bu davranış, yürütme ve hata ayıklama işlemlerini kesmeniz için yeterli zaman sunmayabilir. Bir uygulamada hata ayıklayabilmek için, uygulamayı başlatmak için aşağıdaki yordamlardan birini kullanın:  
  
- Uygulamanız çalışmaya başlar ve bu kesme noktasına ulaşmaz.  
  
- Uygulamanız başlar ve kaynak kodunun ilk satırında hemen kesilir.  
  
- Bir kaynak kodu penceresinde, bir satıra sağ tıklayın ve **imlece Çalıştır**' ı seçin.  
  
   Uygulamanız başlar ve seçilen satıra veya kesme noktasına satırdan önce isabet edildiğinde bir kesme noktasına çalışır.  
  
  Bir konsol uygulamasında hata ayıklarken, uygulamayı Visual Studio 'dan değil komut isteminden başlatmak isteyebilirsiniz. Bu durumda, uygulamayı komut isteminden başlatabilir ve Visual Studio hata ayıklayıcısını buna iliştirebilirsiniz. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
  Visual Studio 'dan bir konsol uygulaması başlattığınızda, **konsol** penceresi bazen Visual Studio penceresinin arkasında görünür. Konsol uygulamanızı Visual Studio 'dan başlatmaya çalışırsanız ve hiçbir şey gerçekleşmezse, Visual Studio penceresini taşımayı deneyin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yerel kodda hata ayıklama](../debugger/debugging-native-code.md)   
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [Visual C++ proje türleri](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
