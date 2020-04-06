---
title: 'Nasıl Yapilir: Yönetilen Kodda Birden Çok İş Parçacığı Yönetme | Microsoft Dokümanlar'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ceaa0af4f57fe374cf9cf4b2dd8b4f40af74a852
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702776"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Nasıl yapılsın: Yönetilen kodda birden çok iş parçacığı yönetme
Eşzamanlı yöntemler çağıran yönetilen bir VSPackage uzantınız varsa veya Visual Studio UI iş parçacığı dışındaki iş parçacıklarında işlem yürüten işlemleri varsa, aşağıda verilen yönergeleri izlemeniz gerekir. Başka bir iş parçacığı üzerinde çalışmanın tamamlanmasını beklemesi gerekmedığından, UI iş parçacığının yanıt vermesini sağlayabilirsiniz. Yığın alanı kaplayan ekstra iş parçacığınız olmadığından ve kilitlenmeleri ve askıları önlemek için hata ayıklama daha güvenilir ve daha kolay hale getirebilirsiniz, çünkü kodunuzu daha verimli hale getirebilirsiniz.

 Genel olarak, UI iş parçacığından farklı bir iş parçacığına veya tam tersi bir konuya geçebilirsiniz. Yöntem döndüğünde, geçerli iş parçacığı ilk çağrıldığı iş parçacığıdır.

> [!IMPORTANT]
> Aşağıdaki yönergeler, <xref:Microsoft.VisualStudio.Threading> ad alanında, özellikle de <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> sınıfta KI API'leri kullanır. Bu ad alanındaki API'ler [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)]''de yenidir. Özellikten <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> bir örnek `ThreadHelper.JoinableTaskFactory`alabilirsiniz.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>UI iş parçacığından arka plan iş parçacığına geçiş

1. Kullanıcı Giçin iş parçacığı üzerindeyseniz ve arka plan iş parçacığı üzerinde `Task.Run()`eşzamanlı çalışma yapmak istiyorsanız, şunları kullanın:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Kullanıcı Birkullanıcı Bilgi Birimi iş parçacığı üzerindeyseniz ve arka plan iş parçacığı üzerinde <xref:System.Threading.Tasks.TaskScheduler> iş `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>yaparken eşzamanlı olarak engellemek istiyorsanız, içindeki özelliği kullanın:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Arka plan iş parçacığından UI iş parçacığına geçiş

1. Bir arka plan iş parçacığı üzerinde iseniz ve UI iş <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>parçacığı üzerinde bir şey yapmak istiyorsanız, kullanın:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     UI iş <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> parçacığına geçmek için yöntemi kullanabilirsiniz. Bu yöntem, geçerli asynchronous yönteminin devamı ile Kullanıcı Bira iş parçacığına bir ileti gönderir ve doğru önceliği ayarlamak ve kilitlenmeleri önlemek için iş parçacığı çerçevesinin geri kalanıyla da iletişim kurar.

     Arka plan iş parçacığı yönteminiz eşzamanlı değilse ve eşzamanlı hale getiremiyorsanız, çalışmanızı `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>şu örnekte olduğu gibi saran kullanıcı arası iş parçacığına geçmek için sözdizimini kullanmaya devam edebilirsiniz:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
