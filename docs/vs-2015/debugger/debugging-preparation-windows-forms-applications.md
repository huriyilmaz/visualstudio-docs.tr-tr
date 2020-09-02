---
title: 'Hata Ayıklama Hazırlığı: Windows Forms uygulamalar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging Windows applications
- Windows applications, debugging
- debugging [Visual Studio], Windows applications
- debugging [J#], Windows applications
- debugging [C#], Windows applications
- debugging [Visual Basic], Windows applications
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 31
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5b11855fbd19dc464f92b4339684ef8346556c21
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691144"
---
# <a name="debugging-preparation-windows-forms-applications"></a>Hata Ayıklama Hazırlığı: Windows Forms Uygulamaları
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms proje şablonu Windows Forms bir uygulama oluşturur. İçinde bu tür bir uygulama hata ayıklaması [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] basittir. Daha fazla bilgi için bkz. [Windows uygulaması projesi oluşturma](https://msdn.microsoft.com/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 Proje şablonuyla bir Windows Forms projesi oluşturduğunuzda, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] otomatik olarak hata ayıklama ve sürüm yapılandırması için gerekli ayarları oluşturur. Gerekirse, bu ayarları değiştirebilirsiniz. Bu ayarlar, ** \<project name> Özellik sayfaları** iletişim kutusunda (Visual Basic**projem** ) değiştirilebilir.  
  
 Daha fazla bilgi için bkz. [Önerilen özellik ayarları](../debugger/managed-debugging-recommended-property-settings.md).  
  
 Aşağıdaki tabloda, önerilen bir ek özellik ayarı görüntülenmektedir.  
  
### <a name="configuration-properties-in-debug-tab"></a>Hata ayıklama sekmesindeki yapılandırma özellikleri  
  
|**Özellik adı**|**Ayar**|  
|-----------------------|-----------------|  
|**Başlatma eylemi**|- **Projenin başlaması** için ayarlanan, çoğu zaman. Hata ayıklamayı başlattığınızda (genellikle dll 'Lerde hata ayıklama için) başka bir yürütülebilir dosya başlatmak istiyorsanız, **dış program Başlat** ' a ayarlayın.|  
  
 Windows Forms uygulamalarında içinden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] veya zaten çalışan bir uygulamaya ekleyerek hata ayıklaması yapabilirsiniz. İliştirme hakkında daha fazla bilgi için bkz. [çalışan Işlemlere ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### <a name="to-debug-a-c-f-or-visual-basic-windows-forms-application"></a>C#, F # veya Visual Basic Windows Forms uygulamasında hata ayıklamak için  
  
1. Projeyi içinde açın [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
2. Gerektiğinde kesme noktaları oluşturun.  
  
    Windows Forms uygulamalar olay odaklı olduğundan, kesme noktalarınız olay işleyicisi koduna veya olay işleyicisi kodu tarafından çağrılan yöntemlere yönlendirilir. Kesme noktalarının yerleştirileceği tipik olaylar şunlardır:  
  
   1. Bir denetimle ilişkili olaylar (örneğin, Click, ENTER vb.)  
  
   2. Yükleme, etkinleştirme vb. uygulama başlatma ve kapatmadan ilişkili olaylar.  
  
   3. Odak ve doğrulama olayları.  
  
      Daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](https://msdn.microsoft.com/library/6514e530-c6b8-489c-a8d2-eda7b7072701).  
  
3. **Hata Ayıkla** menüsünde **Başlat**' a tıklayın.  
  
4. [Hata ayıklayıcı temelleri](../debugger/debugger-basics.md)bölümünde açıklanan teknikleri kullanarak hata ayıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)   
 [C#, F # ve Visual Basic proje türleri](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Nasıl yapılır: hata ayıklama ve yayın yapılandırmasını ayarlama](../debugger/how-to-set-debug-and-release-configurations.md)   
 [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](https://msdn.microsoft.com/library/627df1e9-b254-41af-bbac-9a4f02810c54)
