---
title: 'Nasıl yapılır: DLL projesinde hata ayıklama | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819157"
---
# <a name="how-to-debug-from-a-dll-project"></a>Nasıl Yapılır: DLL Projesinde Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DLL projesinde hata ayıklamaya başlamak için, proje özelliklerinde çağıran uygulamayı belirtmeniz gerekir. C++ Özellik sayfaları, C# ve Visual Basic özellik sayfalarındaki düzen ve içeriklerde farklılık gösterir.  
  
 Yönetilen bir DLL yerel kod tarafından çağrılırsa ve her ikisinde de hata ayıklamak istiyorsanız, bunu proje özelliklerinde belirtebilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> Visual Studio 'nun Express sürümlerinde bir dış çağıran uygulama belirtemezsiniz. Bunun yerine, çözüme yürütülebilir bir proje eklemeniz, başlangıç projesi olarak ayarlamanız ve çalıştırılabilir projeden DLL 'inizdeki yöntemleri çağırmanız gerekir.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Bir C++ projesinde çağıran uygulamayı belirtmek için  
  
1. **Çözüm Gezgini** proje düğümüne sağ tıklayın ve **Özellikler**' i seçin. **Hata Ayıkla** sekmesine gidin.  
  
2. Pencerenin üst kısmındaki **yapılandırma** alanının **hata ayıklama**olarak ayarlandığından emin olun.  
  
3. **Yapılandırma özellikleri/hata ayıklama**bölümüne gidin.  
  
4. **Başlatmak Için hata ayıklayıcı** listesinde, **yerel Windows hata ayıklayıcısı** veya **uzak Windows hata ayıklayıcısı**' nı seçin.  
  
5. **Komut** veya **uzak komut** kutusunda, uygulamanın tam yol adını ekleyin.  
  
6. Gerekli program bağımsız değişkenlerini **komut bağımsız değişkenleri** kutusuna ekleyin.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Bir C# veya Visual Basic projesinde çağıran uygulamayı belirtmek için  
  
1. **Çözüm Gezgini** proje düğümüne sağ tıklayın ve **Özellikler**' i seçin. **Hata Ayıkla** sekmesine gidin.  
  
     **Dış programı Başlat**' ı seçin ve çalıştırılacak programın tam yol adını ekleyin.  
  
     Dış programın komut satırı bağımsız değişkenlerini eklemeniz gerekiyorsa, bunları **komut satırı bağımsız değişkenleri** alanına ekleyin.  
  
2. Ayrıca, bir uygulamayı URL olarak çağırabilirsiniz. (Bir yerel ASP.NET uygulaması tarafından kullanılan yönetilen DLL 'de hata ayıklaması yapıyorsanız bunu yapmak isteyebilirsiniz.)  
  
     **Başlatma eylemi**altında **URL 'de tarayıcıyı Başlat:** radyo düğmesini seçin ve URL 'yi girin.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>DLL projesinden hata ayıklamayı başlatmak için  
  
1. Kesme noktalarını gerektiği gibi ayarlayın.  
  
2. Hata ayıklamayı Başlat (F5 tuşuna basın, yeşil oka tıklayın veya **Hata Ayıkla/hata ayıklamayı Başlat**' a tıklayın).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md)   
 [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
