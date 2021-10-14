---
title: Forms uygulamaları Windows hata ayıklamaya | Microsoft Docs
description: Windows Forms proje şablonu Windows formlarında hata ayıklamak için hazırlık adımlarını Visual Studio.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1cfb5f91196b941dfc14fce1e76bb74cf73a7942
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129971729"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Hata Ayıklama Hazırlığı: Windows Forms Uygulamaları

Windows Forms Uygulaması proje şablonu bir Windows Forms uygulaması oluşturur. içinde bu tür bir uygulamanın hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklaması basittir. Bu tür bir proje oluşturma hakkında bilgi için [bkz. Form Uygulaması Windows oluşturma.](../ide/create-csharp-winform-visual-studio.md)

 Proje şablonuyla bir Windows Forms projesi oluşturursanız, Hata Ayıklama ve Yayın [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] yapılandırmaları için gerekli ayarları otomatik olarak oluşturur. Gerekirse bu ayarları değiştirebilirsiniz. Bu ayarlar Özellik Sayfaları iletişim **\<project name> kutusunda değiştirilebilir** **(** Project Visual Basic).

 Daha fazla bilgi için [bkz. Önerilen Özellik Ayarlar.](../debugger/managed-debugging-recommended-property-settings.md)

 Aşağıdaki tabloda önerilen bir özellik ayarı daha görüntülenir.

### <a name="configuration-properties-in-debug-tab"></a>Hata Ayıklama sekmesindeki Yapılandırma Özellikleri

|**Özellik Adı**|**Ayar**|
|-----------------------|-----------------|
|**Başlatma Eylemi**|- Çoğu **zaman Projeyi başlat** olarak ayarlayın. Hata **ayıklamaya başlarken (genellikle** DLL'lerde hata ayıklama için) başka bir yürütülebilir dosya başlatmak için Dış programı başlat olarak ayarlayın.|

 Uygulamasından veya Windows bir uygulamaya ekerek Form uygulamalarında [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hata ayıkabilirsiniz. Ekleme hakkında daha fazla bilgi için [bkz. Çalışan İşlemlere Ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>Bir C#, F# veya Visual Basic Windows Forms uygulamasında hata ayıklamak için

1. projesini içinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açın.

2. Gerektiğinde kesme noktaları oluşturun.

    Windows Forms uygulamaları olay odaklı olduğundan, kesme noktalarınız olay işleyicisi koduna veya olay işleyicisi kodu tarafından çağrılır yöntemlere gider. Kesme noktalarına yer verilebilecek tipik olaylar şunlardır:

   1. Bir denetimle ilişkili Click, Enter gibi olaylar.

   2. Uygulama başlatma ve kapatma ile ilişkili Yükleme, Etkinleştirildi gibi olaylar.

   3. Odak ve Doğrulama Olayları.

      Daha fazla bilgi için [bkz. Windows Forms'ta Olay İşleyicileri Oluşturma.](/dotnet/framework/winforms/creating-event-handlers-in-windows-forms)

3. Hata **Ayıkla menüsünde** Başlat'a **tıklayın.**

4. Hata ayıklayıcısına ilk bakış konusunda [ele alınan teknikleri kullanarak hata ayıklama.](../debugger/debugger-feature-tour.md)

## <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
- [C#, F# ve Visual Basic Proje Türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Nasıl kullanılır: Hata Ayıklama ve Yayın Yapılandırmalarını Ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)
- [Project Ayarlar C# Hata Ayıklama Yapılandırmaları için Yapılandırmalar](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project Ayarlar Hata Ayıklama Visual Basic için yapılandırma](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Çalıştırma İşlemine İliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Windows Forms](/dotnet/framework/winforms/index)