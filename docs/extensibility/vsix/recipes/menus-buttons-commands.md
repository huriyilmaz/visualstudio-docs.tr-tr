---
title: Menüler & komutları
description: Visual Studio'da menü ve komut sistemi Visual Studio.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: f475a7369050697726dd8a63963c4bc0fb9519a9
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516727"
---
# <a name="adding-menus--commands-to-visual-studio-extensions"></a>Uzantılara & menüler Visual Studio ekleme

Bu makalede, uzantınıza menüler ve komutlar ekleme Visual Studio adım adım Visual Studio sunulmaktadır. Komutlar genellikle menülerin çevresindeki menülerde düğme olarak Visual Studio. Komut oluşturmak için iki adım gerekir:

1. Komutu tanımlama
2. Tıklama/çağırmayı işleme

## <a name="define-the-command"></a>Komutu tanımlama
Her menüde yer alan her düğme bir komuttır. Uzantınıza komut eklemek için önce .vsct dosyasında tanımlamanız gerekir. Şuna benzer olabilir:

```xml
<Buttons>
  <Button guid="MyPackage" id="MyCommand" priority="0x0105" type="Button">
    <Parent guid="VSMainMenu" id="View.DevWindowsGroup.OtherWindows.Group1"/>
    <Icon guid="ImageCatalogGuid" id="StatusInformation" />
    <CommandFlag>IconIsMoniker</CommandFlag>
    <Strings>
      <ButtonText>R&amp;unner Window</ButtonText>
    </Strings>
  </Button>
</Buttons>
```

Bu düğme, öğesinde belirtilen şekilde Görünüm ve Diğer > **Windows** üst gruba `Parent` yerleştirilir.

Şimdi uzantıyı çalıştırarak komutun doğru konumda ve menüde gösterip gösterip görmeyebilirsiniz.

## <a name="handle-the-clickinvocations"></a>Tıklama/çağırmaları işleme
Düğme tanımlandığı zaman ne olacağını işlememiz gerekir. Bunu, şu şekilde görünen bir C# sınıfında yapabiliriz:

```csharp
[Command("489ba882-f600-4c8b-89db-eb366a4ee3b3", 0x0100)]
public class MyCommand : BaseCommand<TestCommand>
{
    protected override Task ExecuteAsync(OleMenuCmdEventArgs e)
    {
        // Do something
    }
}
```

Bunu sınıf yönteminden `Package` çağırarak emin `InitializeAsync` olun.

```csharp
protected override async Task InitializeAsync(CancellationToken cancellationToken, IProgress<ServiceProgressData> progress)
{
    await this.RegisterCommandsAsync();
 }    
```

Guid ve ID komutu, .vsct dosyasındaki öğesinden guid/id `Button` çifti ile eşleşmeli

## <a name="additional-resources"></a>Ek kaynaklar

* [Visual Studio Komut Tablosu (.Vsct) Dosyaları](../../internals/visual-studio-command-table-dot-vsct-files.md)
