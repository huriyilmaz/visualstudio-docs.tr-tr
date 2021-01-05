---
title: Windows Forms uygulamalarda hata ayıklamaya hazırlanma | Microsoft Docs
description: Visual Studio 'da Windows Forms proje şablonu tarafından oluşturulan Windows Forms uygulamalarda hata ayıklamak için hazırlık adımları gerçekleştirin.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3ccb195d6c4a35e4ca3b89c5505ab14c45a5d555
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2020
ms.locfileid: "97726819"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Hata Ayıklama Hazırlığı: Windows Forms Uygulamaları
Windows Forms proje şablonu Windows Forms bir uygulama oluşturur. İçinde bu tür bir uygulama hata ayıklaması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] basittir. Daha fazla bilgi için bkz. [Windows uygulaması projesi oluşturma](/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Proje şablonuyla bir Windows Forms projesi oluşturduğunuzda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] otomatik olarak hata ayıklama ve sürüm yapılandırması için gerekli ayarları oluşturur. Gerekirse, bu ayarları değiştirebilirsiniz. Bu ayarlar, **\<project name> Özellik sayfaları** iletişim kutusunda (Visual Basic **projem** ) değiştirilebilir.

 Daha fazla bilgi için bkz. [Önerilen özellik ayarları](../debugger/managed-debugging-recommended-property-settings.md).

 Aşağıdaki tabloda, önerilen bir ek özellik ayarı görüntülenmektedir.

### <a name="configuration-properties-in-debug-tab"></a>Hata ayıklama sekmesindeki yapılandırma özellikleri

|**Özellik adı**|**Ayar**|
|-----------------------|-----------------|
|**Başlatma eylemi**|- **Projenin başlaması** için ayarlanan, çoğu zaman. Hata ayıklamayı başlattığınızda (genellikle dll 'Lerde hata ayıklama için) başka bir yürütülebilir dosya başlatmak istiyorsanız, **dış program Başlat** ' a ayarlayın.|

 Windows Forms uygulamalarında içinden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] veya zaten çalışan bir uygulamaya ekleyerek hata ayıklaması yapabilirsiniz. İliştirme hakkında daha fazla bilgi için bkz. [çalışan Işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>C#, F # veya Visual Basic Windows Forms uygulamasında hata ayıklamak için

1. Projeyi içinde açın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

2. Gerektiğinde kesme noktaları oluşturun.

    Windows Forms uygulamalar olay odaklı olduğundan, kesme noktalarınız olay işleyicisi koduna veya olay işleyicisi kodu tarafından çağrılan yöntemlere yönlendirilir. Kesme noktalarının yerleştirileceği tipik olaylar şunlardır:

   1. Bir denetimle ilişkili olaylar (örneğin, Click, ENTER vb.)

   2. Yükleme, etkinleştirme vb. uygulama başlatma ve kapatmadan ilişkili olaylar.

   3. Odak ve doğrulama olayları.

      Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms).

3. **Hata Ayıkla** menüsünde **Başlat**' a tıklayın.

4. Hata [ayıklayıcıyla ilk bakış](../debugger/debugger-feature-tour.md)bölümünde açıklanan teknikleri kullanarak hata ayıklayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)
- [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)