---
title: Windows Forms uygulamalarda hata ayıklamaya hazırlanma | Microsoft Docs
ms.custom: seodec18
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
ms.openlocfilehash: 5ff927e5b917834341e442afa00e4acad4af2d2f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738093"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Hata Ayıklama Hazırlığı: Windows Forms Uygulamaları
Windows Forms proje şablonu Windows Forms bir uygulama oluşturur. @No__t_0 içinde bu tür bir uygulama için hata ayıklama basittir. Daha fazla bilgi için bkz. [Windows uygulaması projesi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 Proje şablonuyla bir Windows Forms projesi oluşturduğunuzda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıklama ve yayın yapılandırmalarına yönelik gerekli ayarları otomatik olarak oluşturur. Gerekirse, bu ayarları değiştirebilirsiniz. Bu ayarlar **\<project ad > Özellik sayfaları** iletişim kutusunda (Visual Basic**projem** ) değiştirilebilir.

 Daha fazla bilgi için bkz. [Önerilen özellik ayarları](../debugger/managed-debugging-recommended-property-settings.md).

 Aşağıdaki tabloda, önerilen bir ek özellik ayarı görüntülenmektedir.

### <a name="configuration-properties-in-debug-tab"></a>Hata ayıklama sekmesindeki yapılandırma özellikleri

|**Özellik adı**|**Ayarlanmasını**|
|-----------------------|-----------------|
|**Başlatma eylemi**|- **Projenin başlaması** için ayarlanan, çoğu zaman. Hata ayıklamayı başlattığınızda (genellikle dll 'Lerde hata ayıklama için) başka bir yürütülebilir dosya başlatmak istiyorsanız, **dış program Başlat** ' a ayarlayın.|

 Windows Forms uygulamalarında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] içinden veya zaten çalışan bir uygulamaya ekleyerek hata ayıklaması yapabilirsiniz. İliştirme hakkında daha fazla bilgi için bkz. [çalışan Işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Bir C#, F#veya Visual Basic Windows Forms uygulamada hata ayıklamak için

1. Projeyi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açın.

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
- [Nasıl Yapılır: Hata Ayıklama ve Dağıtım Yapılandırmalarını Ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)
- [C# Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)