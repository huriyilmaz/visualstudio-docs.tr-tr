---
title: İlerleme durumu gösteriliyor
description: Farklı ilerleme çubukları türlerini ve bunların her biri ne zaman kullanacağız?
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 872876dd0a2785b991abf846399f3519193409f6
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516596"
---
# <a name="progress-bars-for-backgrounds-tasks-in-visual-studio-extensions"></a>Uzantılarda arka plan görevleri için ilerleme Visual Studio çubukları

Çalışan bir arka plan görevinin ilerlemesini bu görevlerde göstermenin birkaç Visual Studio. Kendi uzantılarınıza ait ilerleme çubuklarını nasıl kullanabileceğinizi burada bulabilirsiniz.

## <a name="status-bar"></a>Durum çubuğu
Durum çubuğu kendi ilerleme göstergesine sahip ve kullanıcıya ilerleme durumunu göstermek için en kolay yerdir. Görünür durumdadır, ancak kullanıcının dikkatini çekmesini veya geçerli görevini engellemesini talep etmemektedir. Durum çubuğu, çoğu arka plan görevi için iyi bir seçenektir.

:::image type="content" source="../media/status-bar-progress.gif" alt-text="Kullanım durumundaki durum çubuğu ilerleme göstergesinin animasyonu.":::

Durum çubuğu ilerleme durumunu göstermek için API kullanmak oldukça basittir:

```csharp
await Task.Delay(1000); // long running task
await VS.StatusBar.ShowProgressAsync("Step 1/3", 1, 3);

await Task.Delay(1000); // long running task
await VS.StatusBar.ShowProgressAsync("Step 2/3", 2, 3);

await Task.Delay(1000); // long running task
await VS.StatusBar.ShowProgressAsync("Step 3/3", 3, 3);

// Progress ends as current step (3) and total steps (3) are equal
```

## <a name="threaded-wait-dialog"></a>İş Parçacıklı Bekleme İletişim Kutusu
İş Parçacıklı Bekleme İletişim Kutusu (TWD), yalnızca arka plan görevi genişletici tarafından belirtilen x saniyeden uzun sürerse açılan bir ilerleme göstergesi iletişim kutusu. İlerleme durumunu durum çubuğuna tüm süre boyunca yazar, ancak x saniyenin ardından iletişim kutusunu gösterir.

:::image type="content" source="../media/threaded-wait-dialog.gif" alt-text="İlerlemeyi gösteren İş Parçacıklı Bekleme İletişim Kutusu.":::

TWD, istediğiniz zaman gösterilmez. Son kullanıcıya Visual Studio müdahale etmey şeklinde yönetilen bir uygulamadır. Bunu kullanmak yalnızca durum çubuğunu kullanmaktan daha fazla kod gerektirir, ancak yine de kullanımı nispeten basit bir API'dir:  

```csharp
var fac = await VS.Services.GetThreadedWaitDialogAsync() as IVsThreadedWaitDialogFactory;
IVsThreadedWaitDialog4 twd = fac.CreateInstance();

twd.StartWaitDialog("Demo", "Working on it...", "", null, "", 1, true, true);

var totalSteps = 3;

for (var currentStep = 1; currentStep <= totalSteps; currentStep++)
{
    var text = $"Step {currentStep}/{totalSteps}";
    twd.UpdateProgress("In progress", text, text, currentStep, totalSteps, true, out _);

    await Task.Delay(1000); // long running task

    if (currentStep == totalSteps)
    {
        // Dismisses the dialog
        (twd as IDisposable).Dispose();
    }
}
```

## <a name="task-status-center"></a>Görev Durumu Merkezi
Durum çubuğunun sol alt köşesinde Görev Durumu Merkezi (TSC). Uzun süre çalışan arka plan görevleriyle ilgili ilerlemeyi rapor etmek için kullanılır ve Visual Studio.

:::image type="content" source="../media/task-status-center.gif" alt-text="Görev Durumu Merkezi arka plan görevi gösteriliyor.":::

API'nin, ilerlemeyi göstermek için diğer yöntemleri kullanmaktan daha fazla kavramı vardır.

```csharp
private async Task StartAsync()
{
    IVsTaskStatusCenterService tsc = await VS.Services.GetTaskStatusCenterAsync();

    var options = default(TaskHandlerOptions);
    options.Title = "My long running task";
    options.ActionsAfterCompletion = CompletionActions.None;

    TaskProgressData data = default;
    data.CanBeCanceled = true;

    ITaskHandler handler = tsc.PreRegister(options, data);
    Task task = LongRunningTaskAsync(data, handler);
    handler.RegisterTask(task);
}

private async Task LongRunningTaskAsync(TaskProgressData data, ITaskHandler handler)
{
    float totalSteps = 3;

    for (float currentStep = 1; currentStep <= totalSteps; currentStep++)
    {
        await Task.Delay(1000);

        data.PercentComplete = (int)(currentStep / totalSteps * 100);
        data.ProgressText = $"Step {currentStep} of {totalSteps} completed";
        handler.Progress.Report(data);
    }
}
```

## <a name="other-resources"></a>Diğer kaynaklar

* [Görev Durumu Merkezi API başvurusu](/dotnet/api/microsoft.visualstudio.taskstatuscenter)
