---
title: Mac için Visual Studio’yu Genişletme
description: Mac için Visual Studio özellikleri ve işlevleri, uzantı paketleri olarak adlandırılan modüllerle genişletilebilir. Bu kılavuzun ilk bölümü, bir belgeye tarih ve saat eklemek için basit bir Mac için Visual Studio uzantısı paketi oluşturur. Bu kılavuzun ikinci bölümünde, Uzantı paketi sisteminin temelleri ve Mac için Visual Studio temelini oluşturan bazı çekirdek API 'Leri tanıtılmıştır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/07/2019
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 76f8f4945542d1b2fd4dce230d750db4c965af76
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74983261"
---
# <a name="extending-visual-studio-for-mac"></a>Mac için Visual Studio’yu Genişletme

Mac için Visual Studio, *uzantı paketleri*olarak adlandırılan bir modül kümesinden oluşur. Uzantı paketlerini, ek bir dil veya yeni bir proje şablonu için destek gibi Mac için Visual Studio yeni işlevler tanıtmak için kullanabilirsiniz.

Uzantı paketleri diğer uzantı paketlerinin *uzantı* noktalarından oluşturur. Uzantı noktaları, bir menü veya IDE komutları listesi gibi, üzerine genişletilebilen alanlara yönelik yer tutuculardır. Uzantı paketi, yeni bir menü öğesi veya yeni bir komut gibi bir uzantı olarak adlandırılan yapılandırılmış verilerin bir düğümünü kaydederek bir uzantı noktasından derleyebilir. Her uzantı noktası, *komut*, *panel*veya *dosya şablonu*gibi belirli tür uzantıları kabul eder. Uzantı noktaları içeren bir modüle, diğer uzantı paketleri tarafından genişletila, *eklenti Konağı*denir.

Mac için Visual Studio özelleştirmek için, aşağıdaki diyagramda gösterildiği gibi, Mac için Visual Studio önceden var olan kitaplıkların içindeki eklenti konaklarından bulunan uzantı noktalarından bulunan uzantı paketleri oluşturabilirsiniz:

![Eklenti mimarisi](media/extending-visual-studio-mac-addin1.png)

Bir uzantı paketinin Mac için Visual Studio derlemesi için, Mac için Visual Studio IDE içindeki önceden var olan uzantı noktalarından oluşturan uzantılara sahip olması gerekir. Bir uzantı paketi, eklenti konağında tanımlı bir uzantı noktasını temel aldığında, bu uzantı paketinde bir _bağımlılık_ sahip olduğu söylenir.

Bu modüler tasarımın avantajı Mac için Visual Studio Genişletilebilir olduğundan, özel uzantı paketleriyle birlikte derleyebilen birçok uzantı noktası vardır. Geçerli uzantı paketlerine örnek olarak, ve C# F#hata ayıklayıcı araçları ve proje şablonları için destek verilebilir.

> [!NOTE]
> Eklenti Oluşturucu 1,2 ' den önce oluşturulmuş bir eklenti Oluşturucu projeniz varsa, [Aşağıdaki adımlarda açıklandığı](https://mhut.ch/addinmaker/1.2)gibi projenizi geçirmeniz gerekir.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Bu bölüm, eklenti Oluşturucu tarafından oluşturulan farklı dosyalara ve bir komut uzantısının gerektirdiği verilere bakar.

## <a name="attribute-files"></a>Öznitelik dosyaları

Uzantı paketleri ad, sürüm, bağımlılıklar ve diğer bilgilerle ilgili meta verileri C# özniteliklerde depolar. Eklenti Oluşturucu, bu bilgileri depolamak ve düzenlemek için `AddinInfo.cs` ve `AssemblyInfo.cs` iki dosya oluşturur. Uzantı paketleri *`Addin` özniteliğinde*belirtilen BENZERSIZ bir kimliğe ve ad alanına sahip olmalıdır:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Uzantı paketleri ayrıca derleme zamanında otomatik olarak başvurulan uzantı noktalarına sahip olan uzantı paketlerinde bağımlılıklar bildirmelidir.

Ayrıca, aşağıdaki görüntüde gösterildiği gibi, projenin çözüm panelindeki eklenti başvurusu düğümü aracılığıyla ek başvurular eklenebilir:

![Tarih Ekle ekran görüntüsü](media/extending-visual-studio-mac-addin13.png)

Ayrıca, bunlara karşılık gelen `assembly:AddinDependency` öznitelikleri derleme zamanında eklenir. Meta veriler ve bağımlılık bildirimleri olduktan sonra, uzantı paketinin temel yapı taşlarına odaklanırsınız.

## <a name="extensions-and-extension-points"></a>Uzantılar ve uzantı noktaları

Uzantı noktası, bir veri yapısını (bir tür) tanımlayan bir yer tutucudur, ancak uzantı belirli bir uzantı noktası tarafından belirtilen yapıya uygun olan verileri tanımlar. Uzantı noktaları, bildiriminde kabul edebilecekleri uzantı türünü belirtir. Uzantılar, tür adları veya uzantı yolları kullanılarak bildirilmiştir. İhtiyaç duyduğunuz uzantı noktasının nasıl oluşturulacağı hakkında daha ayrıntılı bir açıklama için [uzantı noktası başvurusuna](https://github.com/mono/mono-addins/wiki/Extension-Points) bakın.

Uzantı/uzantı noktası mimarisi Mac için Visual Studio hızlı ve modüler geliştirmeyi korur.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Komut uzantıları

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Komut uzantıları, her yürütüldüğünde çağrılan yöntemlere işaret eden uzantılardır.

Komut uzantıları, `/MonoDevelop/Ide/Commands` uzantı noktasına girdi eklenerek tanımlanır. Aşağıdaki kodla `Manifest.addin.xml` uzantımızı tanımlıyoruz:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Uzantı düğümü, içinde bulunduğu uzantı noktasını belirten bir yol özniteliği içerir, bu durumda `/MonoDevelop/Ide/Commands/Edit`. Ayrıca, komutuna bir üst düğüm işlevi görür. Komut düğümü aşağıdaki özniteliklere sahiptir:

* `id`-bu komut için tanımlayıcıyı belirtir. Komut tanımlayıcıları, numaralandırma üyeleri olarak bildirilmelidir ve komutları Commandıtems 'lara 'e bağlamak için kullanılır.
* `_label`-menülerde gösterilecek metin.
* `_description`-araç çubuğu düğmeleri için araç ipucu olarak gösterilecek metin.
* `defaultHandler`-komutu destekleyen `CommandHandler` sınıfını belirtir

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

`/MonoDevelop/Ide/MainMenu/Edit` uzantı noktasına takılan bir CommandItem uzantısı aşağıdaki kod parçacığında gösterilmiştir:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem, `id` özniteliğinde belirtilen bir komutu bir menüye koyar. Bu CommandItem, komut etiketinin **düzenleme menüsünde**görünmesini sağlayan `/MonoDevelop/Ide/MainMenu/Edit` uzantı noktasını genişlettidir. CommandItem içindeki KIMLIğIN, `InsertDate`komut düğümünün KIMLIĞINE karşılık geldiğini unutmayın. CommandItem öğesini kaldırırsanız, düzenleme menüsünde **Tarih Ekle** seçeneği kaybolur.

### <a name="command-handlers"></a>Komut Işleyicileri

`InsertDateHandler`, `CommandHandler` sınıfının bir uzantısıdır. `Update` ve `Run`iki yöntemi geçersiz kılar. `Update` yöntemi, bir komut bir menüde gösterildiğinde veya anahtar bağlamaları aracılığıyla yürütüldüğünde sorgulanır. Bilgi nesnesini değiştirerek, komutu devre dışı bırakabilir veya görünmez yapabilir, dizi komutlarını doldurabilir ve daha fazlasını yapabilirsiniz. Bu `Update` yöntemi, içine metin eklemek için bir *TextEditor* ile etkin bir *belge* bulamazsa komutu devre dışı bırakır:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Yalnızca komutu etkinleştirmek veya gizlemek için özel mantığın olması durumunda `Update` yöntemini geçersiz kılmanız gerekir. `Run` yöntemi, bir Kullanıcı bir komutu her çalıştırdığında yürütülür ve bu durumda Kullanıcı düzenleme menüsünden komutu seçtiğinde oluşur. Bu yöntem, metin düzenleyicisinde giriş işaretine tarih ve saat ekler:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Komut türünü `DateInserterCommands`bir numaralandırma üyesi olarak bildirin:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Komut ve CommandItem artık birlikte bağlanır; **düzenleme menüsünden**CommandItem seçildiğinde CommandItem komutu çağırır.

## <a name="ide-apis"></a>IDE API 'Leri

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Geliştirme için kullanılabilen alanların kapsamı hakkında bilgi için bkz. [uzantı ağacı başvurusu](https://www.monodevelop.com/developers/articles/extension-tree-reference/) ve [API 'ye genel bakış](https://www.monodevelop.com/developers/articles/api-overview/). Gelişmiş uzantı paketleri oluştururken de [Geliştirici makalelerine](https://www.monodevelop.com/developers/articles/)bakın. Özelleştirme için alanların kısmi bir listesi aşağıda verilmiştir:

* La
* Anahtar bağlama şemaları
* İlkeler
* Kod biçimleri
* Proje dosyası biçimleri
* Tercihler bölmeleri
* Seçenek bölmeleri
* Hata ayıklayıcı protokolleri
* Hata ayıklayıcı Görselleştiriciler
* Çalışma alanı düzenleri
* Çözüm paneli ağaç düğümleri
* Kaynak Düzenleyicisi kenar boşlukları
* Birim testi altyapıları
* Kod oluşturucuları
* Kod parçacıkları
* Hedef çerçeveler
* Hedef çalışma zamanı
* VCS arka uçlar
* Yeniden Düzenle
* Yürütme işleyicileri
* Söz dizimi vurgulama

## <a name="extending-the-new-editor"></a>Yeni düzenleyiciyi genişletme

Mac için Visual Studio, Windows üzerinde Visual Studio ile aynı düzenleyici katmanlarının üzerine inşa eden [Yeni bir yerel Cocoa metin Düzenleyicisi Kullanıcı arabirimi tanıtır](https://aka.ms/vs/mac/editor/learn-more) .

Visual Studio ve Mac için Visual Studio arasında düzenleyiciyi paylaşmanın birçok avantajı, Visual Studio Düzenleyicisi 'ni hedefleyen kodun Mac için Visual Studio çalışmak üzere uyarlanabilmesinin bir avantajlarından biridir.

> [!NOTE]
> Yeni düzenleyici şu anda yalnızca C# dosyaları destekler. Diğer diller ve dosya biçimleri eski düzenleyicide açılır. Eski düzenleyici ancak aşağıda açıklanan Visual Studio Düzenleyicisi API 'Lerinden bazılarını uygular.

### <a name="visual-studio-editor-overview"></a>Visual Studio düzenleyicisine genel bakış

![Visual Studio Düzenleyicisi mimarisi](media/vs-editor-architecture.png)

Mac için Visual Studio 'e özgü uzantı ayrıntılarına dokunmadan önce, paylaşılan düzenleyicinin kendisi hakkında daha fazla bilgi edinmek faydalı olur. Aşağıda, bu anlama göz duymasına sebep olabilecek birkaç kaynak verilmiştir:

* [Managed Extensibility Framework](/dotnet/framework/mef/index)
* [Düzenleyicide MEF](/visualstudio/extensibility/managed-extensibility-framework-in-the-editor)
* [Düzenleyicinin İçinde](/visualstudio/extensibility/inside-the-editor)
* [Dil Hizmeti ve Düzenleyici Uzantı Noktaları](/visualstudio/extensibility/language-service-and-editor-extension-points)
* [Düzenleyici mimarisine bir video giriş](https://www.youtube.com/watch?v=PkYVztKjO9A)

Birlikte bu kaynaklarla, bilmeniz gereken birincil kavramlar bir [`ITextBuffer`](/dotnet/api/microsoft.visualstudio.text.itextbuffer) ve [`ITextView`](/dotnet/api/microsoft.visualstudio.text.editor.itextview):

* `ITextBuffer`, zaman içinde değiştirilebilen metnin bellek içi gösterimidir. `ITextBuffer` `CurrentSnapshot` özelliği, `ITextSnapshot`bir örneği olan arabelleğin geçerli içeriğinin *sabit* bir gösterimini döndürür. Arabellekte bir düzenleme yapıldığında CurrentSnapshot özelliği en son sürüme güncelleştirilir. Çözümleyiciler, herhangi bir iş parçacığında metin anlık görüntüsünü inceleyebilir ve içeriği hiçbir şekilde değişmemelidir.

* `ITextView`, düzenleyici denetimindeki `ITextBuffer` 'in ekranda nasıl işlendiğine ilişkin kullanıcı arabirimi gösterimidir. Metin arabelleğinin yanı sıra `Caret`, `Selection`ve diğer kullanıcı arabirimi ile ilgili kavramlara bir başvuru içerir.

Belirli bir [`MonoDevelop.Ide.Gui.Document`](http://source.monodevelop.com/#MonoDevelop.Ide/MonoDevelop.Ide.Gui/Document.cs,4e960d4735f089b5)için, ilişkili temel `ITextBuffer` ve `ITextView` sırasıyla `Document.GetContent<ITextBuffer>()` ve `Document.GetContent<ITextView>()` aracılığıyla alabilirsiniz.

## <a name="additional-information"></a>Ek Bilgiler

> [!NOTE]
> Şu anda Mac için Visual Studio için genişletilebilirlik senaryolarını geliştirmeye çalışıyoruz. Uzantılar oluşturuyorsanız ve ek yardım veya bilgilere ihtiyacınız varsa veya geri bildirim sağlamak istiyorsanız, lütfen [Mac için Visual Studio uzantısı yazma](https://aka.ms/vsmac-extensions-survey) formunu girin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio uzantıları geliştirme (Windows üzerinde)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
