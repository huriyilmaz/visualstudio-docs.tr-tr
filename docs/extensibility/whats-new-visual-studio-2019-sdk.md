---
title: Visual Studio 2019 SDK 'daki yenilikler | Microsoft Docs
description: Visual Studio SDK, düzenleyici kayıt geliştirmeleri dahil olmak üzere Visual Studio 2019 için yeni ve güncelleştirilmiş özellikleri içerir.
ms.custom: SEO-VS-2020
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3ca803eb330f0640910e271ec5bf531de0ccdf58
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122028403"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK 'daki yenilikler

Visual Studio SDK, Visual Studio 2019 için aşağıdaki yeni ve güncelleştirilmiş özelliklere sahiptir.

## <a name="synchronously-autoloaded-extensions-warning"></a>Zaman uyumlu olarak yüklenen uzantılar uyarısı

Kullanıcılar, yüklü uzantılarından herhangi biri zaman uyumlu olarak başlangıçta tekrar yüklenirse bir uyarı görür. [Zaman uyumlu olarak yüklenen uzantılara](synchronously-autoloaded-extensions.md)uyarı hakkında daha fazla bilgi edinebilirsiniz.

## <a name="single-unified-visual-studio-sdk"></a>tek, birleşik Visual Studio SDK

artık tüm Visual Studio SDK varlıklarını, [Microsoft. VisualStudio. SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk)tek bir NuGet paketi aracılığıyla edinebilirsiniz.

## <a name="editor-registration-enhancements"></a>Düzenleyici kayıt geliştirmeleri

oluşturulduktan sonra, Visual Studio bir düzenleyicinin belirli uzantılar (örneğin,. xaml ve. rc) için benzeşimini bildirebileceği veya herhangi bir uzantı için uygun olduğu özel düzenleyici kaydı desteklendiğinden (. *). Visual Studio 2019 sürüm 16,1 ' den başlayarak, düzenleyici kaydı desteğini genişlettik.

### <a name="filenames"></a>Dosya Adları

Belirli bir dosya uzantısı için destek kaydetme veya buna ek olarak, bir düzenleyici yeni özniteliği düzenleyicinin paketine uygulayarak belirli dosya adlarını desteklemeyi kaydedebilir `ProvideEditorFilename` .

Örneğin, tüm. JSON dosyalarını destekleyen bir düzenleyici, bu `ProvideEditorExtension` özniteliği paketine uygular:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

16,1 ile başlayarak, MyEditor yalnızca birkaç iyi bilinen. json dosyasını destekliyorsa, bunun yerine bu `ProvideEditorFilename` öznitelikleri pakete uygulayabilir:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>Uıcontexts

Bir düzenleyici, ne zaman etkinleştirildiğini temsil eden bir veya daha fazla Uiconmetini kaydedebilir. Uiconmetin'ler, düzenleyiciyi kaydeden pakete bir veya daha fazla örneği uygulanarak kaydedilir `ProvideEditorUIContextAttribute` .

Bir düzenleyicide Uiconmetin'ler kayıtlıysa:

- Verilen uzantıya sahip bir dosya açıldığında en az bir kayıtlı Uiconmetinlerinden biri etkinse düzenleyici, düzenleyici aramasına dahil edilir.
- Kayıtlı Uiconmetinlerinde hiçbiri etkin değilse düzenleyici, düzenleyici aramasına dahil edilmez.

Bir düzenleyici hiçbir Uiconmetin'i KAYDETMEZSE, bu uzantı için her zaman düzenleyici aramasına dahil edilir.

Örneğin, bir düzenleyici yalnızca bir C# projesi açık olduğunda kullanılabiliyorsa, bir öznitelik uygulayarak bu benzeşimi bildirebilirler `ProvideEditorUIContext` :

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
