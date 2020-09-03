---
title: Bir DLL projesinden hata ayıklama | Microsoft Docs
ms.date: 10/10/2018
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 081e897b0ff76dd97d2c174bf8c6fbfa2334f8ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350127"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Nasıl yapılır: Visual Studio 'da DLL projesinde hata ayıklama (C#, C++, Visual Basic, F #)

DLL projesinde hata ayıklamanın bir yolu, çağıran uygulamayı DLL proje özelliklerinde belirtmektir. Daha sonra DLL projesinden hata ayıklamaya başlayabilirsiniz. Bu yöntemin çalışması için, uygulamanın, yapılandırdığınız aynı konumda aynı DLL 'yi çağırması gerekir. Uygulama DLL 'nin farklı bir sürümünü bulup yüklerse, bu sürüm kesme noktalarınız içermez. Dll 'Leri hata ayıklamanın diğer yöntemleri için bkz. [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md).

Yönetilen uygulamanız yerel bir DLL 'yi çağırırsa veya yerel uygulamanız yönetilen bir DLL 'yi çağırırsa, hem DLL hem de çağıran uygulamada hata ayıklaması yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: karışık modda hata ayıklama](../debugger/how-to-debug-in-mixed-mode.md).

Yerel ve yönetilen DLL projelerinin çağıran uygulamaları belirtmek için farklı ayarları vardır.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Yerel DLL projesinde çağıran uygulama belirtme

1. **Çözüm Gezgini**' de C++ DLL projesini seçin. **Özellikler** simgesini seçin, **alt** + **ENTER**tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. ** \<Project> Özellik sayfaları** iletişim kutusunda pencerenin üst kısmındaki **yapılandırma** alanının **hata ayıklama**olarak ayarlandığından emin olun.

1. **Yapılandırma özellikleri**  >  **hata ayıklamayı**seçin.

1. **Başlatmak Için hata ayıklayıcı** listesinde, **yerel Windows hata ayıklayıcısı** veya **uzak Windows hata ayıklayıcısı**' nı seçin.

1. **Komut** veya **uzak komut** kutusunda, çağıran uygulamanın tam yolunu ve dosya adını (örneğin, *. exe* dosyası) ekleyin.

   ![Hata ayıklama Özellikler penceresi](../debugger/media/dbg-debugging-properties-dll.png "Hata ayıklama Özellikler penceresi")

1. Gerekli program bağımsız değişkenlerini **komut bağımsız değişkenleri** kutusuna ekleyin.

1. **Tamam**’ı seçin.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Yönetilen DLL projesinde çağıran uygulama belirtme

1. **Çözüm Gezgini**' de C# veya Visual Basic DLL projesi seçin. **Özellikler** simgesini seçin, **alt** + **ENTER**tuşuna basın veya sağ tıklayıp **Özellikler**' i seçin.

1. Pencerenin üst kısmındaki **yapılandırma** alanının **hata ayıklama**olarak ayarlandığından emin olun.

1. **Başlangıç eylemi**altında:

   - .NET Framework dll 'Ler için **dış program Başlat**' ı seçin ve çağıran uygulamanın tam yolunu ve adını ekleyin.

   - Ya da, **TARAYıCıYı URL Ile Başlat** ' ı seçin ve yerel bir ASP.NET uygulamasının URL 'sini girin.

   - .NET Core dll 'Leri için **hata ayıklama** özellikleri sayfası farklıdır. **Başlat** açılan menüsünde **çalıştırılabilir** ' i seçin ve ardından çağıran uygulamanın tam yolunu ve adını **çalıştırılabilir** alana ekleyin.

1. Gerekli komut satırı bağımsız değişkenlerini **komut satırı bağımsız değişkenlerine** veya **uygulama bağımsız** değişkenleri alanına ekleyin.

   ![C# hata ayıklama Özellikler penceresi](../debugger/media/dbg-debugging-properties-dll-csharp.png "C# hata ayıklama Özellikler penceresi")

1. **File**  >  Değişiklikleri kaydetmek için**Seçili öğeleri kaydet** veya **CTRL** + **S** dosyalarını kullanın.

## <a name="debug-from-the-dll-project"></a>DLL projesinden hata ayıkla

1. DLL projesinde kesme noktaları ayarlayın.

1. DLL projesine sağ tıklayın ve **Başlangıç projesi olarak ayarla**' yı seçin.

1. **Çözüm yapılandırma** alanının **Hata Ayıkla**olarak ayarlandığından emin olun. **F5**tuşuna basın, yeşil **Başlangıç** okuna tıklayın veya hata ayıklama **Debug**  >  **başlatma hata ayıklaması**' nı seçin.

Hata ayıklama kesme noktalarınız isabet aldıysa, DLL çıkışlarınızın (varsayılan olarak, * \<project> \debug* klasörü) çağıran uygulamanın çağrıldığı konum olduğundan emin olun.

## <a name="see-also"></a>Ayrıca bkz.
- [DLL projelerinde hata ayıklama](../debugger/debugging-dll-projects.md)
- [C# hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Visual Basic hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [C++ hata ayıklama yapılandırması proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)