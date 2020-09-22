---
title: OnStart yönteminde hata ayıkla | Microsoft Docs
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
ms.openlocfilehash: d695e4d22c728eb256aeb0e1350819ba23b93385
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852380"
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

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. **Evet, hata ayıkla ' yı seçin \<service name> .**

4. Tam zamanında hata ayıklayıcı penceresinde, hata ayıklama için kullanmak istediğiniz Visual Studio sürümünü seçin.

    ![Ettintimedebugger](../debugger/media/justintimedebugger.png "Ettintimedebugger")

5. Visual Studio 'nun yeni bir örneği başlar ve yöntem sırasında yürütme durdurulur `Debugger.Launch()` .

## <a name="see-also"></a>Ayrıca bkz.
- [Hata Ayıklama Güvenliği](../debugger/debugger-security.md)
- [Yönetilen Kodda Hata Ayıklama](../debugger/debugging-managed-code.md)
