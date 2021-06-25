---
title: 'Nasıl yapılır: yönetilen kodda birden çok Iş parçacığını yönetme | Microsoft Docs'
description: Yönetilen VSPackage uzantınız zaman uyumsuz yöntemleri çağırırsa veya Visual Studio UI iş parçacığı üzerinde işlemler varsa, kodda birden çok iş parçacığını yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 39319b748dd41c6936e7b70e20243202452fae67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112903092"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Nasıl yapılır: yönetilen kodda birden çok iş parçacığını yönetme
Zaman uyumsuz yöntemleri çağıran veya Visual Studio UI iş parçacığı dışındaki iş parçacıklarında yürütülen işlemler içeren bir yönetilen VSPackage uzantınız varsa, aşağıda verilen yönergeleri izlemelisiniz. Başka bir iş parçacığında çalışmanın tamamlanmasını beklemek zorunda olmadığından UI iş parçacığını yanıt vermeye devam edebilirsiniz. Yığın alanı alan ek iş parçacıklarından ve hata ayıklamadan ve yanıt vermeyen koddan emin olmadığınız için kodunuzu daha verimli hale getirebilirsiniz.

 Genel olarak, UI iş parçacığından farklı bir iş parçacığına geçiş yapabilir veya tam tersi de geçerlidir. Yöntem döndüğünde, geçerli iş parçacığı ilk olarak çağrıldığı iş parçacığıdır.

> [!IMPORTANT]
> Aşağıdaki kılavuzlar, özel ad alanındaki API 'Leri, <xref:Microsoft.VisualStudio.Threading> özellikle <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> sınıfında kullanır. Bu ad alanındaki API 'Ler sürümünde yenidir [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] . Özelliğinden bir örneğini alabilirsiniz <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory` .

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>UI iş parçacığından arka plan iş parçacığına geçiş yap

1. UI iş parçacığında çalışıyorsanız ve bir arka plan iş parçacığında zaman uyumsuz çalışma yapmak istiyorsanız şunu kullanın `Task.Run()` :

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. UI iş parçacığında çalışıyorsanız ve bir arka plan iş parçacığında iş gerçekleştirirken zaman uyumlu olarak engellemek istiyorsanız, <xref:System.Threading.Tasks.TaskScheduler> içindeki özelliği kullanın `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> :

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Bir arka plan iş parçacığından UI iş parçacığına geçiş yap

1. Bir arka plan iş parçacığı kullanıyorsanız ve Kullanıcı arabirimi iş parçacığında bir şey yapmak istiyorsanız şunu kullanın <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> :

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>Yöntemini kullanarak UI iş parçacığına geçiş yapabilirsiniz. Bu yöntem, geçerli zaman uyumsuz yöntemin devamlılığı ile UI iş parçacığına bir ileti gönderir ve ayrıca doğru önceliği ayarlamak ve kilitlenmeleri önlemek için iş parçacığı çerçevesinin geri kalanı ile iletişim kurar.

     Arka plan iş parçacığı yönteminiz zaman uyumsuz değilse ve bunu zaman uyumsuz hale getirmek istiyorsanız, `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> Bu örnekte olduğu gibi, birlikte çalışmanızı SARMALAYARAK Kullanıcı arabirimi iş parçacığına geçiş yapmak için söz dizimini kullanabilirsiniz:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
