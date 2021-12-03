---
title: Bildirimler
description: Kullanıcılara bildirimleri göstermenin farklı yollarının tarifi.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: d0b38d963bb3a0c80aee1f43b06afb5fa142d1a3
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516662"
---
# <a name="displaying-notifications-in-visual-studio-extensions"></a>Bildirim uzantılarında Visual Studio görüntüleme

Uzantınızı kullanıcıya bildirim görüntülemeye ilişkin çeşitli mekanizmalar vardır. Doğru seçeneği seçmek zor olabilir, bu nedenle seçeneklere bakalım.

* Durum çubuğu
* Bilgi çubuğu
* İleti kutusu
* Çıktı penceresi

Bunlar farklı amaçlar için kullanılır ve kullanıcıların dikkatini çeken farklı talep düzeylerine sahiptir.

Kullanıcıya **herhangi bir** eylem veya giriş gerektirmeyen bir olayı bildirmek için durum çubuğunu kullanın. Durum çubuğunda bildirimi kaçırırsa bu sorun değil. Bunu görmeleri kritik öneme sahip değildi.

Kullanıcının dikkatini çekmek ve bu kullanıcılara bazı eylemler sunmak için bilgi çubuğunu **kullanın.** Bu işi hemen yapmaları gerekm yok, yapacakları işi yapana kadar bekleyebilirler. Bildirim önemlidir, ancak kritik değildir.

Bildirimin geçerli kullanıcının ne yaptığına devam ettiğini engellemesi gerekirken, bir ileti **kutusu kullanın.** Bu bir engelleme ve kritik bildirimdir.

Kullanıcıya kritik olmayan hatalar hakkında bilgi için **Çıkış Penceresi.** Kullanıcıların bunu gördüğünden emin Çıkış Penceresi ama bunu yapmamanız önerilir.

## <a name="status-bar"></a>Durum çubuğu
Durum çubuğu, birincil pencerenin alt kısmında bulunan ve geçerli pencerenin durumu (nelerin görüntü altında olduğu ve nasıl görüntü olduğu gibi), arka plan görevleri (yazdırma, tarama ve biçimlendirme gibi) veya diğer bağlamsal bilgileri (seçim ve klavye durumu gibi) görüntüleyen bir alandır.

:::image type="content" source="../media/status-bar.png" alt-text="Özel metni gösteren durum çubuğu.":::

Durum çubuğunu, kullanıcının tüm dikkatini çekmeniz gerekmasa da, yine de onlara bilgi vermek için kullanın.

### <a name="set-the-text"></a>Metni ayarlama
Bu, durum çubuğundaki metni herhangi bir dizeye ayarlar.

```csharp
// call it from an async context
await VS.StatusBar.ShowMessageAsync("My text");

// or from a synchronous method:
VS.StatusBar.ShowMessageAsync("My text").FireAndForget();
```

### <a name="animation-icon"></a>Animasyon simgesi
Durum çubuğuna animasyon simgesi eklemek kolaydır.

:::image type="content" source="../media/status-bar-animation.gif" alt-text="StatusAnimation.Sync simgesi kullanılarak animasyonu yapılan durum çubuğu.":::

Tek yapmanız gereken, hangi animasyon simgesinin kullanılamayacaklarını belirtmektir.

```csharp
// call it from an async context
await VS.StatusBar.StartAnimationAsync(StatusAnimation.Sync);

// or from a synchronous method:
VS.StatusBar.StartAnimationAsync(StatusAnimation.Sync).FireAndForget();
```

çağrısıyla animasyonu yeniden `EndStatusbarAnimationAsync` durdurun.

```csharp
// call it from an async context
await VS.StatusBar.EndAnimationAsync(StatusAnimation.Sync);

// or from a synchronous method:
VS.StatusBar.EndAnimationAsync(StatusAnimation.Sync).FireAndForget();
```

## <a name="info-bar"></a>Bilgi çubuğu
Bilgi Çubuğu, bir araç veya belge penceresinin üst kısmında yer alan sarı bir çubuktır. Kullanıcının dikkatini engellemeden çekmek için kullanışlıdır. Bilgi Çubuğu bir simge, metin ve birkaç köprü içerebilir.

:::image type="content" source="../media/info-bar-solution-explorer.png" alt-text="Bir bilgi çubuğunda gösterilen bilgi Çözüm Gezgini.":::

Çözüm Gezgini araç penceresine Bilgi Çubuğu Çözüm Gezgini edinebilirsiniz.

```csharp
var model = new InfoBarModel(
    new[] {
        new InfoBarTextSpan("The text in the Info Bar. "),
        new InfoBarHyperlink("Click me")
    },
    KnownMonikers.PlayStepGroup,
    true);

InfoBar infoBar = VS.InfoBar.CreateInfoBar(ToolWindowGuids80.SolutionExplorer, model);
infoBar.ActionItemClicked += InfoBar_ActionItemClicked;
await infoBar.TryShowInfoBarUIAsync();

...

private void InfoBar_ActionItemClicked(object sender, InfoBarActionItemEventArgs e)
{
    ThreadHelper.ThrowIfNotOnUIThread();

    if (e.ActionItem.Text == "Click me")
    {
        // do something
    }
}
```

Belge penceresine Bilgi Çubuğu eklemek için yöntemine açık bir belgenin dosya adını eklemeniz `VS.Notifications.CreateInfoBar(fileName, model)` gerekir.

:::image type="content" source="../media/info-bar-document.png" alt-text="Bir belgenin üst kısmında gösterilen Bilgi Çubuğu.":::

Bilgi Çubuğunu doğrudan bir ile yapmak için `ITextView` bu kullanışlı uzantı yöntemini kullanabilirsiniz:

```csharp
InfoBar infoBar = textView.CreateInfoBar(model);
```

## <a name="message-box"></a>İleti kutusu
.NET kullanarak ileti kutusu göstermenin çeşitli yolları vardır. Örneğin, Windows Forms veya WPF aracılığıyla. Ana pencerede üst öğe Visual Studio uzantılarında bazı sorunlara neden olur, bu nedenle kendi ileti Visual Studio kullanılması önerilir.

:::image type="content" source="../media/message-box.png" alt-text="Yerel Visual Studio ileti kutusu.":::

Kullanıcının tüm dikkatini çekmek için kullanıcı arabirimini engellemeniz gereken bir ileti kutusu kullanın.

```csharp
// Simple text box
VS.MessageBox.Show("Title", "The message");

// Async and with buttons defined
await VS.MessageBox.ShowAsync("Title", "The message", OLEMSGICON.OLEMSGICON_INFO, OLEMSGBUTTON.OLEMSGBUTTON_OKCANCEL);   
```

## <a name="output-window"></a>Çıktı Penceresi
Özel durumlar ve Çıkış Penceresi metinsel bilgiler hakkında bilgi görüntülemek için Çıkış Penceresi'i kullanın.

:::image type="content" source="../media/output-window.png" alt-text="Özel bölmeye yazılan Çıkış Penceresi.":::

özel bir Çıkış Penceresi oluşturmak ve bu bölmeye yazmak, yöntemi kullanılarak doğrudan ileriye doğru `VS.Windows.CreateOutputWindowPaneAsync` uzer.

```csharp
OutputWindowPane pane = await VS.Windows.CreateOutputWindowPaneAsync("Name of pane");
await pane.WriteLineAsync("Line 1");
await pane.WriteLineAsync("Line 2");
await pane.WriteLineAsync("Line 3");

```

Özel durumları [günlüğe kaydetme hakkında daha](handle-errors.md) fazla bilgi için hata işleme tarifine bakın.
