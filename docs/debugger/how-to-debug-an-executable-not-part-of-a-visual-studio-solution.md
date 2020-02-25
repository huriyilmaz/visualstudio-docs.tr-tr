---
title: Visual Studio çözümünün parçası olmayan bir uygulamanın hatalarını ayıklamak
titleSuffix: ''
ms.custom: ''
ms.date: 02/21/2020
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 740af718a2928991d46bedbd6709337b9b20a254
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557906"
---
# <a name="debug-an-app-that-isnt-part-of-a-visual-studio-solution-c-c-visual-basic-f"></a>Visual Studio çözümünün parçası olmayan bir uygulamanın hatalarını ayıklamak (C++, C#, Visual Basic F#)

Visual Studio çözümünün parçası olmayan bir uygulamada ( *. exe* dosyası) hata ayıklamak isteyebilirsiniz. Bu bir [açık klasör](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) projesi veya sizin ya da başka birinin uygulamayı Visual Studio dışında oluşturmuş olabileceği gibi, başka bir yerde de uygulamayı oluşturmuş olabilirsiniz.

- Visual Studio 'da (proje veya çözüm dosyası olmayan) bir açık klasör projesi için, bkz. [kodunuzu çalıştırma ve hata ayıklama](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md#run-and-debug-your-code) veya for C++The [Launch. vs. JSON ile hata ayıklama parametrelerini yapılandırma](/cpp/build/open-folder-projects-cpp#configure-debugging-parameters-with-launchvsjson).

- Visual Studio 'da mevcut olmayan bir uygulama için, hata ayıklamanın her bir yolu, uygulamayı Visual Studio dışında başlatmak ve sonra Visual Studio hata ayıklayıcısında **Işleme Ekle** ' yi kullanarak buna eklemektir. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

   Bir uygulamaya ekleme, birkaç saniye sürebilir el ile yapılacak adımlar gerektirir. Bu gecikme nedeniyle ekleme bir başlatma sorunu hataları ayıklamanıza yardımcı olmaz veya kullanıcı için beklemez bir uygulama girin ve hızlı şekilde biten.

   Bu durumda, uygulama için bir Visual Studio EXE projesi oluşturabilir, veya varolan içine alma C#, Visual Basic veya C++ çözüm. Programlama dillerinin tümü EXE projelerini desteklemez.

>[!IMPORTANT]
>Uygulamaya ekleme ya da Visual Studio çözüme ekleme Visual Studio'da tasarlanmadı bir uygulama için hata ayıklama özellikleri sınırlıdır.
>
>Kaynak kodu varsa, en iyi yaklaşım bir Visual Studio projesine kod aktarmaktır. Ardından, uygulamayı hata ayıklama yapısını çalıştırın.
>
>Kaynak kodunuz yoksa ve uygulamanın, uyumlu bir biçimde [hata ayıklama bilgileri](../debugger/how-to-set-debug-and-release-configurations.md) yoksa, kullanılabilir hata ayıklama özellikleri çok az olabilir.

### <a name="to-create-a-new-exe-project-for-an-existing-app"></a>Var olan bir uygulama için yeni bir EXE projesi oluşturmak için

1. Visual Studio 'da **dosya** >  > projesi **Aç** 'ı seçin.

1. **Proje Aç** Iletişim kutusunda **dosya adı**' nın yanındaki açılan listede, önceden seçili değilse, **tüm proje dosyaları**' nı seçin.

1. *. Exe* dosyasına gidin, seçin ve **Aç**' ı seçin.

   Dosya, yeni, geçici bir Visual Studio çözümü içinde görünür.

1. **Hata ayıklama menüsünden hata** **ayıklamayı Başlat**gibi bir yürütme komutu seçerek uygulamada hata ayıklamayı başlatın.

### <a name="to-import-an-app-into-an-existing-visual-studio-solution"></a>Bir uygulama var olan bir Visual Studio çözümüne aktarmak için

1. Visual Studio C++'da C#bir, veya Visual Basic çözüm açıkken **Dosya** >  > **var olan projeyi** **Ekle** ' yi seçin.

1. **Proje Aç** Iletişim kutusunda **dosya adı**' nın yanındaki açılan listede, önceden seçili değilse, **tüm proje dosyaları**' nı seçin.

1. *. Exe* dosyasına gidin, seçin ve **Aç**' ı seçin.

   Dosya, geçerli çözüm altında yeni bir proje olarak görüntülenir.

1. Yeni dosya seçili **olduğunda hata ayıklama menüsünden hata** **ayıklamayı Başlat**gibi bir yürütme komutu seçerek uygulamada hata ayıklamayı başlatın.

### <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)
- [Hata ayıklayıcısı güvenliği](../debugger/debugger-security.md)
- [DBG dosyaları](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))