---
title: Dosyalarla çalışma
description: İpuçları çalışmak için kullanılır.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 80d0c7265be8bb833ef07fcde8e0baaa0ec8eb2a
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516584"
---
# <a name="working-with-files-and-documents-in-visual-studio-extensions"></a>Uzantılarda dosya ve belgelerle Visual Studio çalışma

Dosya ve belgelerle çalışmanın farklı yollarına sahip küçük kod örnekleri koleksiyonu burada vemektedir.

## <a name="get-active-text-view"></a>Etkin metin görünümünü al
Metin arabelleği metnini değiştirmek için geçerli etkin metin görünümünü alma.

```csharp
DocumentView docView = await VS.Documents.GetActiveDocumentViewAsync();
if (docView?.TextView == null) return; //not a text window
SnapshotPoint position = docView.TextView.Caret.Position.BufferPosition;
docView.TextBuffer?.Insert(position, "some text"); // Inserts text at the caret
```

## <a name="file-icon-associations"></a>Dosya simgesi ilişkilendirmeleri
Bir simgeyi dosya uzantısıyla ilişkilendirmek Çözüm Gezgini, `[ProvideFileIcon()]` özniteliğini paket sınıfınıza ekleyin.

```csharp
[ProvideFileIcon(".abc", "KnownMonikers.Reference")]
public sealed class MyPackage : ToolkitPackage
{
    ...
}
```

Bilinen BilinenLer Gezgini araç penceresini `KnownMonikers` kullanarak koleksiyonda bulunan binlerce simgeye bakın. Ana menüde **Görünüm > Diğer Windows** altında bulabilirsiniz.

## <a name="open-file"></a>Dosyayı açma
Yardımcı `Microsoft.VisualStudio.Shell.VsShellUtilities` sınıfını kullanın.

```csharp
string fileName = "c:\\file.txt";
await VS.Document.OpenAsync(fileName);
```

## <a name="open-file-via-project"></a>Proje aracılığıyla dosya açma
Açmakta olduğu dosya çözümün bir parçası olduğunda bu yöntemi kullanın.

```csharp
string fileName = "c:\\file.txt";
await VS.Documents.OpenViaProjectAsync(fileName);
```

## <a name="open-file-in-preview-tab"></a>Dosyayı Önizleme sekmesinde açma
Sağlama sekmesi olarak da bilinen Önizleme sekmesi, belge iyinin sağ tarafında açılan geçici bir sekmedir. Önizleme sekmesinde aşağıdaki gibi herhangi bir dosyayı açın:

```csharp
string fileName = "c:\\file.txt";
await VS.Documents.OpenInPreviewTabAsync(fileName);
```

## <a name="get-file-name-from-itextbuffer"></a>ITextBuffer'dan dosya adı al
Ad alanı içinde `buffer.GetFileName()` bulunan genişletme yöntemini `Microsoft.VisualStudio.Text` kullanın.

```csharp
string fileName = buffer.GetFileName();
```

## <a name="solutionitem-from-file"></a>Dosyadan SolutionItem
Mutlak `SolutionItem` dosya yolundan dosyasını bulun.

```csharp
string fileName = "c:\\file.txt";
PhysicalFile item = await PhysicalFile.FromFileAsync(fileName);
```
