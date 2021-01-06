---
title: OnStart yönteminde hata ayıkla | Microsoft Docs
description: Visual Studio 'da bir Windows hizmetinin OnStart yönteminde hata ayıklamanın, yöntemin içinden hata ayıklayıcıyı başlatarak nasıl yapılacağını öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 488fe471552256e8fad62bb6f831448811ca343f
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903148"
---
# <a name="how-to-debug-the-onstart-method"></a>Nasıl Yapılır: OnStart Yönteminde Hata Ayıklama
Hizmeti başlatarak ve hata ayıklayıcıyı hizmet sürecine ekleyerek bir Windows hizmetinde hata ayıklaması yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Ancak, <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> bir Windows hizmeti yönteminde hata ayıklamak için, hata ayıklayıcıyı yöntemin içinden başlatmanız gerekir.

1. Yönteminin başına öğesine bir çağrı ekleyin <xref:System.Diagnostics.Debugger.Launch%2A> `OnStart()` .

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Hizmeti başlatın ( `net start` **Hizmetler** penceresinde kullanabilir veya başlatabilirsiniz).

    Aşağıdakine benzer bir iletişim kutusu görmeniz gerekir:

    ![Bir Visual Studio tam zamanında hata ayıklayıcı iletişim kutusunun, WindowsService-Asis.exe içinde işlenmemiş bir .NET Framework özel durumu gösteren ekran görüntüsü.](../debugger/media/onstartdebug.png)

3. **Evet, hata ayıkla ' yı seçin \<service name> .**

4. Tam zamanında hata ayıklayıcı penceresinde, hata ayıklama için kullanmak istediğiniz Visual Studio sürümünü seçin.

    ![Olası hata ayıklayıcılar listesinde ' Microsoft Visual Studio 2015 ' yeni örneğini içeren bir Visual Studio tam zamanında hata ayıklayıcı penceresinin ekran görüntüsü.](../debugger/media/justintimedebugger.png)

5. Visual Studio 'nun yeni bir örneği başlar ve yöntem sırasında yürütme durdurulur `Debugger.Launch()` .

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcı güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
