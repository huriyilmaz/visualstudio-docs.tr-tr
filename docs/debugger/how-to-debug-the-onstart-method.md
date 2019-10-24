---
title: 'Nasıl yapılır: OnStart yönteminde hata ayıklama | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 107ce6d5ca2b327d77fe588e1ac7ffda10a0a3a3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733623"
---
# <a name="how-to-debug-the-onstart-method"></a>Nasıl Yapılır: OnStart Yönteminde Hata Ayıklama
Hizmeti başlatarak ve hata ayıklayıcıyı hizmet sürecine ekleyerek bir Windows hizmetinde hata ayıklaması yapabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Windows hizmet uygulamalarında hata ayıklama](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Ancak, bir Windows hizmetinin <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> yönteminde hata ayıklamak için, hata ayıklayıcıyı yöntemin içinden başlatmanız gerekir.

1. @No__t_1method başına <xref:System.Diagnostics.Debugger.Launch%2A> bir çağrı ekleyin.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Hizmeti başlatın (`net start` kullanabilir veya **Hizmetler** penceresinde başlatabilirsiniz).

    Aşağıdakine benzer bir iletişim kutusu görmeniz gerekir:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. **Evet, hata ayıkla \<service adı > seçin.**

4. Tam zamanında hata ayıklayıcı penceresinde, hata ayıklama için kullanmak istediğiniz Visual Studio sürümünü seçin.

    ![Ettintimedebugger](../debugger/media/justintimedebugger.png "Ettintimedebugger")

5. Visual Studio 'nun yeni bir örneği başlar ve `Debugger.Launch()` yönteminde yürütme durdurulur.

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklayıcısı Güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
