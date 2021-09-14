---
title: 'Nasıl: Yönetilen Kodda Birden Çok İş Parçacığını Yönetme | Microsoft Docs'
description: Yönetilen VSPackage uzantınız zaman uyumsuz yöntemler çağırıyorsa veya kullanıcı arabirimi iş parçacığında işlem varsa kodda birden çok iş parçacığını Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8bc6cdae2ac2fca16467bdbeee2333e7d7189ee9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724967"
---
# <a name="how-to-manage-multiple-threads-in-managed-code"></a>Nasıllı: Yönetilen kodda birden çok iş parçacığını yönetme
Zaman uyumsuz yöntemleri çağıran veya Visual Studio kullanıcı arabirimi iş parçacığı dışında iş parçacıklarında yürütülen işlemlere sahip yönetilen bir VSPackage uzantınız varsa, aşağıda verilen yönergeleri izlemeniz gerekir. Kullanıcı arabirimi iş parçacığının yanıt verme işleminin tamamlanması için başka bir iş parçacığında iş parçacığını beklemesi gerekmay olduğundan bu iş parçacığını tutabilirsiniz. Yığın alanı alan fazladan iş parçacıklarınız olmadığı için kodunuzu daha verimli hale getirir ve kilitlenmeleri ve yanıt vermemeye çalışan kodu önleyene kadar daha güvenilir ve hata ayıklamayı daha kolay hale getirirsiniz.

 Genel olarak, kullanıcı arabirimi iş parçacığından farklı bir iş parçacığına (veya tam tersi) geçiş yapabilirsiniz. yöntem döndür geldiğinde, geçerli iş parçacığı başlangıçta çağrıldı olduğu iş parçacığıdır.

> [!IMPORTANT]
> Aşağıdaki yönergeler, özellikle sınıfındaki <xref:Microsoft.VisualStudio.Threading> ad alanı API'lerini <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> kullanır. Bu ad alanı api'leri içinde [!INCLUDE[vs_dev12](../extensibility/includes/vs_dev12_md.md)] yenidir. özelliğinden bir örneği <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> <xref:Microsoft.VisualStudio.Shell.ThreadHelper> `ThreadHelper.JoinableTaskFactory` eldeabilirsiniz.

## <a name="switch-from-the-ui-thread-to-a-background-thread"></a>Ui iş parçacığından arka plan iş parçacığına geçme

1. Kullanıcı arabirimi iş parçacığındaysanız ve bir arka plan iş parçacığında zaman uyumsuz çalışma yapmak için `Task.Run()` kullanın:

    ```csharp
    await Task.Run(async delegate{
        // Now you're on a separate thread.
    });
    // Now you're back on the UI thread.

    ```

2. Kullanıcı arabirimi iş parçacığındaysanız ve arka plan iş parçacığı üzerinde çalışma yaparken zaman uyumlu olarak engellemek için içindeki <xref:System.Threading.Tasks.TaskScheduler> özelliğini `TaskScheduler.Default` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> kullanın:

    ```csharp
    // using Microsoft.VisualStudio.Threading;
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        await TaskScheduler.Default;
        // You're now on a separate thread.
        DoSomethingSynchronous();
        await OrSomethingAsynchronous();
    });
    ```

## <a name="switch-from-a-background-thread-to-the-ui-thread"></a>Arka plan iş parçacığından UI iş parçacığına geçme

1. Bir arka plan iş parçacığındaysanız ve kullanıcı arabirimi iş parçacığında bir şey yapmak için <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> kullanın:

    ```csharp
    // Switch to main thread
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
    ```

     Kullanıcı arabirimi iş <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> parçacığına geçmek için yöntemini kullanabilirsiniz. Bu yöntem, geçerli zaman uyumsuz yöntemin devamı ile kullanıcı arabirimi iş parçacığına bir ileti iletir ve ayrıca doğru önceliği ayarlamak ve kilitlenmeleri önlemek için iş parçacığı çerçevesinin geri kalanıyla iletişim kurar.

     Arka plan iş parçacığı yönteminiz zaman uyumsuz değilse ve zaman uyumsuz değilse, bu örnekte olduğu gibi çalışmanızı ile sarmalamanız ile kullanıcı arabirimi iş parçacığına geçiş yapmak için söz dizimini kullanmaya `await` <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A> devam edersiniz:

    ```csharp
    ThreadHelper.JoinableTaskFactory.Run(async delegate {
        // Switch to main thread
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();
        // Do your work on the main thread here.
    });
    ```
