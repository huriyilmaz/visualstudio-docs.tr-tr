---
title: Visual Studio 2019 SDK'da Yenilikler | Microsoft Dokümanlar
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740406"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK'da Yenilikler

Visual Studio SDK, Visual Studio 2019 için aşağıdaki yeni ve güncel özelliklere sahiptir.

## <a name="synchronously-autoloaded-extensions-warning"></a>Eşzamanlı otomatik yüklenmiş uzantılar uyarısı

Kullanıcılar artık yüklü uzantılarından herhangi birinin başlangıçta eşzamanlı olarak otomatik olarak yüklenmesi durumunda bir uyarı görürler. [Sen Synchronously otomatik yüklü uzantıları](synchronously-autoloaded-extensions.md)de uyarı hakkında daha fazla bilgi edinebilirsiniz.

## <a name="single-unified-visual-studio-sdk"></a>Tek, birleşik Visual Studio SDK

Artık tek bir NuGet paketi [Microsoft.VisualStudio.SDK](https://www.nuget.org/packages/microsoft.visualstudio.sdk)aracılığıyla tüm Visual Studio SDK varlıkları alabilirsiniz.

## <a name="editor-registration-enhancements"></a>Editör Kayıt Geliştirmeleri

Visual Studio, kuruluşundan bu yana, bir editörün belirli uzantılara (örneğin, .xaml ve .rc) olan yakınlığını beyan edebileceği veya herhangi bir uzantı için uygun olduğu (.*) özel editör kaydını desteklemiştir. Visual Studio 2019 sürüm 16.1'den başlayarak editör kaydı desteğini genişletiyoruz.

### <a name="filenames"></a>Dosya Adları

Belirli bir dosya uzantısı için destek kaydetmenin yanı sıra veya bunun yerine, düzenleyicinin paketine `ProvideEditorFilename` yeni öznitelik uygulayarak belirli dosya adlarını desteklediğini kaydedebilir.

Örneğin, tüm .json dosyalarını destekleyen bir `ProvideEditorExtension` düzenleyici bu özniteliği paketine uygular:

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

16.1 ile başlayarak, MyEditor yalnızca birkaç iyi bilinen .json dosyasını `ProvideEditorFilename` destekliyorsa, bunun yerine bu öznitelikleri paketine uygulayabilir:

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

Bir düzenleyici, etkinleştirildiğinde temsil eden bir veya daha fazla UIContexts kaydedebilir. Kullanıcı Arabirimi Bağlamları, düzenleyiciyi kaydeden `ProvideEditorUIContextAttribute` pakete bir veya daha fazla örnek uygulanarak kaydedilir.

Bir düzenleyici Kullanıcı Arabirimi'ni kaydettirmişse:

- Kayıtlı UIContexts en az biri verilen uzantı ile bir dosya açıldığında etkin ise, düzenleyici arama dahil edilir.
- Kayıtlı Kullanıcı Arabirimi İçeriklerinin hiçbiri etkin değilse, düzenleyici düzenleyici aramaya dahil edilmez.

Bir düzenleyici herhangi bir UIContexts kaydetmiyorsa, her zaman bu uzantı için düzenleyici arama dahildir.

Örneğin, bir düzenleyici yalnızca Bir C# projesi açık olduğunda kullanılabilirse, bir `ProvideEditorUIContext` öznitelik uygulayarak bu yakınlığı bildirebilir:

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
