---
title: İlk uzantınız
description: İlk uzantınızı çalıştırmaya ve çalıştırmaya Visual Studio adımlarını gösterir.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: f9fabafbc1bf99e07827e02618b5c3e267265860
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516772"
---
# <a name="your-first-visual-studio-extension"></a>İlk Visual Studio uzantınız

Bu makalede, ilk çalışma uzantınızı çalıştırmaya yardımcı olacak Visual Studio adım adım açıklanmıştır. Visual Studio uzantısı, .NET Framework ve C# kullanılarak yazılır. Zaten bir .NET geliştiricisiyseniz, uzantı yazmanın diğer .NET programlarının ve kitaplıklarının çoğunu yazmaya benzer olduğunu bulabilirsiniz.

Bugün yazmakta olacağınız uzantı, yürütülürken metin düzenleyicisine yeni bir guid ekleyen bir komut ekler. Basit, kullanışlı ve uzantı geliştirmenin çeşitli yönlerine iyi bir giriş sağlar.

Görsel öğrenenlerden biriysiniz, öğreticiyi takip eden birinin bu kısa videosuna göz at.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWPmjK]

İlk uzantınızı yazmaya Visual Studio önce (çok kolay, söz! ! ) gerekli araçları [](get-tools.md)edinenin.

## <a name="create-the-project"></a>Proje oluşturma
Seçecek birkaç proje şablonu vardır, bu nedenle doğru seçimi yapmak istiyorsanız. Bu topluluk araç setsinde kullanılan şablonların hepsinde ad olarak bilinen **Community (Community)** vardır.

VSIX **Project Komutu (Community)** şablonu, bağlı bir komutla birlikte gelir ve buradan başlamayı kolaylaştırır. Bu, çoğu uzantı için harika bir başlangıç noktasıdır. Araç penceresi kullanmak istediğinizi biliyorsanız VSIX Project Araç Penceresi **(Community) şablonunu** kullanın. Araç penceresini açmak için bir komutu da vardır.

Yalnızca **MEF uzantıları veya diğer Community** için Boş VSIX Project **(Community) veya VSIX Project (Community)** şablonlarını kullanın.

Bu kez, aşağıdaki ekran görüntüsünde **gösterildiği gibi VSIX Project komutu (Community)** şablonunu seçerek.

:::image type="content" source="../media/new-project-dialog.png" alt-text="VSIX Project şablonlarını gösteren Yeni Uygulama İletişim Kutusu.":::

Proje şablonunu seçdikten sonra projenize bir ad verebilirsiniz. **InsertGuid olarak anma.**

:::image type="content" source="../media/configure-new-project.png" alt-text="Yeni projenizi yapılandırma.":::

Oluştur düğmesine **bastığınızda** aşağıdaki gibi bir temel VSIX Project oluşturmanız gerekir:

:::image type="content" source="../media/new-project-files.png" alt-text="Yeni proje dosyaları ve klasörleri.":::

## <a name="overview-of-the-files"></a>Dosyalara genel bakış
Şimdi en önemli dosyaların üzerinden bakalım.

**InsertGuidPackage.cs,** Package sınıfı olarak adlandırılır. Yöntemi, `InitializeAsync(...)` uzantınızı başlatmak Visual Studio tarafından çağrılır. Burada olay dinleyicileri eklip komutlarını, araç pencerelerini, ayarları ve diğer şeyleri kaydedebilirsiniz.

**source.extension.vsixmanifest,** uzantınız için bildirim dosyasıdır. Başlık ve açıklama gibi meta verilerin yanı sıra uzantının içeriği hakkında da bilgi içerir.

**VSCommandTable.vsct,** komutların ve anahtar bağlamalarının bildirimli bir şekilde tanımlandığı ve bu nedenle komutlara kaydedilebiliyor olduğu bir XML Visual Studio.

**Commands/MyCommand.cs,** *VSCommandTable.vsct* dosyasında tanımlanan komutun komut işleyicisidir. Düğmeye tıklayarak komut yürütülürken ne olacağını kontrol eder.

## <a name="modifying-the-command"></a>Komutu değiştirme
İlk olarak, komut satırı menü sistemi içinde doğru adı, simgeyi ve konumu Visual Studio gerekir.

*VSCommandTable.vsct dosyasını* açın ve bir ve `<Group>` `<Button>` bulun. Düğmenin grubu üst öğe olarak, grubun üst öğesinin ise yerleşik *VSMainMenu/Araçlar* menüsü olduğunu fark edin.

Uzantınız için *GUID* Ekle komut düğmesinin Ana  menüyü düzenle altında yer almak istediğiniz için grubu Düzenle menüsüne yeniden üst öğe olarak ekleyebilirsiniz. Aşağıdaki *kod* *parçacığında olduğu* gibi Araçları Düzenle ile değiştirin:

```xml
<Group guid="InsertGuid" id="MyMenuGroup" priority="0x0600">
  <Parent guid="VSMainMenu" id="Edit"/>
</Group>
```

Doğru yeri bulmayı kolaylaştıran yerleştirmeler için tam IntelliSense elde edebilirsiniz.

:::image type="content" source="../media/vsct-parent-intellisense.png" alt-text="VSCT üst IntelliSense.":::

Bu `<Button>` ihtiyaçların da güncelleştiriliyor olması gerekir. Öğenin özniteliğini `id` PasteAppend olarak güncelleştirerek yeni `<Icon>` bir simge *vereceksiniz.* Metni iyi, açıklayıcı bir adla güncelleştirin ve komutunun teknik adıyla güncelleştirin. Bu ad, Araçlar > Seçenekler > Environment > Klavye iletişim kutusunda komutunıza özel klavye kısayolları atarken kullanıcılara gösterilen `<ButtonText>` `<LocCanonicalName>` addır. 

```xml
<Button guid="InsertGuid" id="MyCommand" priority="0x0100" type="Button">
  <Parent guid="InsertGuid" id="MyMenuGroup" />
  <Icon guid="ImageCatalogGuid" id="PasteAppend" />
  <CommandFlag>IconIsMoniker</CommandFlag>
  <Strings>
    <ButtonText>Insert GUID</ButtonText>
    <LocCanonicalName>.Edit.InsertGuid</LocCanonicalName>
  </Strings>
</Button>
```

>[!NOTE]
> her zaman nokta `<LocCanonicalName>` karakteriyle başlar. Başka hiçbir metin otomatik olarak önceden kaleme alındı ve nokta gösterilmez.  

Visual Studio'nin görüntü kitaplığında bulunan binlerce simgeyi kullanabilir ve hatta IntelliSense'te gösterilen bir önizlemeyi elde edebilirsiniz:

:::image type="content" source="../media/vsct-icon-intellisense.png" alt-text="VSCT simgesi IntelliSense.":::

Şimdi komutun adını, simgesini ve konumunu güncelleştirildi ve şimdi metin düzenleyicisine guid eklemek için kod yazma zamanı geldi.

*/Commands/MyCommand.cs* dosyasını açın ve yürütülürken yeni bir guid eklemek için dosyayı değiştirebilirsiniz:

```csharp
using System;
using Community.VisualStudio.Toolkit;
using EnvDTE;
using Microsoft.VisualStudio.Shell;
using Task = System.Threading.Tasks.Task;

namespace InsertGuid
{
    [Command(PackageIds.MyCommand)]
    internal sealed class MyCommand : BaseCommand<MyCommand>
    {
        protected override async Task ExecuteAsync(OleMenuCmdEventArgs e)
        {
            await Package.JoinableTaskFactory.SwitchToMainThreadAsync();
            DocumentView docView = await VS.Documents.GetActiveDocumentViewAsync();
            if (docView?.TextView == null) return;
            SnapshotPoint position = docView.TextView.Caret.Position.BufferPosition;
            docView.TextBuffer?.Insert(position, Guid.NewGuid().ToString()); 
        }
    }
}
```

Etkin düzenleyici metin görünümünü almak için nesnesini kullanıyor ve ardından guid'i metin arabelleğinin `VS` dikkati konumunda ekli olarak ekleyebilirsiniz.

>[!NOTE]
> Bu topluluk araç `await JoinableTaskFactory.SwitchToMainThreadAsync()` `ThreadHelper.ThrowIfNotOnUIThread()` setlerinde birçok yerde ve 'i göreceğiz. İş parçacığı değiştirmenin en iyi uygulamalarını ele almaktadırlar ve bu noktada bunları ne zaman ve nasıl kullanabileceğiniz konusunda bilginiz yok. Kod Düzeltmeleri (ampuller) ile derleyici uyarıları bunu çok kolaylaştırır.

Uzantımızın ilk taslağı tamamlandı ve artık bunu test etmek için zamanı geldi.

## <a name="running-and-debugging"></a>Çalıştırma ve hata ayıklama
Uzantınızı çalıştırmanız, diğer .NET projelerini çalıştırmanız kadar kolaydır. Hata *ayıklayıcı eklenmiş şekilde* çalıştırmak için F5'e veya olmadan çalıştırmak *için Ctrl+F5* tuşlarına basın.

Bunu yapmak, uzantınız yüklü Visual Studio Deneysel Örnek'i başlatacak. Deneysel Örnek, ayrı ayarlar ve uzantılar Visual Studio normal sürümünüzdür. Her şeyi ayrı tutmanıza yardımcı olur.

Deneysel Örnek başlatıldığında Düzenle ana menüsünde *GUID* Ekle komutunu *görüyor* gerekir.

:::image type="content" source="../media/insert-guid-command.png" alt-text="Ana menüyü düzenle'de bulunan GUID ekle komutu.":::

Metin tabanlı herhangi bir dosyayı açın ve yeni bir GUID eklemek için komutunu yürütün. İşte bu kadar!

## <a name="summary"></a>Özet
Ana menüye bir komut düğmesi ekleyen ve yürütülürken metin düzenleyicisiyle etkileşime olan ilk uzantınızı oluşturdunız.

Tebrikler!!

Bu uzantının kodunu örnek deposunda [bulabilirsiniz.](https://github.com/VsixCommunity/Samples)

## <a name="additional-resources"></a>Ek kaynaklar

* [Uzantıların anatomisi](extension-anatomy.md)
* [Menüler & Komutları](../recipes/menus-buttons-commands.md)
* [En iyi yöntemler denetim listesi](../publish/checklist.md)
