---
title: Mac için Visual Studio’yu Genişletme
description: Mac için Visual Studio özellikleri ve işlevleri, uzantı paketleri olarak adlandırılan modüllerle genişletilebilir. Bu kılavuzun ilk bölümü, bir belgeye tarih ve saat eklemek için basit bir Mac için Visual Studio uzantısı paketi oluşturur. Bu kılavuzun ikinci bölümünde, Uzantı paketi sisteminin temelleri ve Mac için Visual Studio temelini oluşturan bazı çekirdek API 'Leri tanıtılmıştır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 29c5bb9c45ae8d859316bd9c63eec10a6a425571
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851965"
---
# <a name="extending-visual-studio-for-mac"></a>Mac için Visual Studio’yu Genişletme

Mac için Visual Studio, *uzantı paketleri*olarak adlandırılan bir modül kümesinden oluşur. Uzantı paketlerini, ek bir dil veya yeni bir proje şablonu için destek gibi Mac için Visual Studio yeni işlevler tanıtmak için kullanabilirsiniz.

Uzantı paketleri diğer uzantı paketlerinin *uzantı* noktalarından oluşturur. Uzantı noktaları, bir menü veya IDE komutları listesi gibi, üzerine genişletilebilen alanlara yönelik yer tutuculardır. Uzantı paketi, yeni bir menü öğesi veya yeni bir komut gibi bir uzantı olarak adlandırılan yapılandırılmış verilerin bir düğümünü kaydederek bir uzantı noktasından derleyebilir. Her uzantı noktası, *komut*, *panel*veya *dosya şablonu*gibi belirli tür uzantıları kabul eder. Uzantı noktaları içeren bir modüle, diğer uzantı paketleri tarafından genişletila, *eklenti Konağı*denir.

Mac için Visual Studio özelleştirmek için, aşağıdaki diyagramda gösterildiği gibi, Mac için Visual Studio önceden var olan kitaplıkların içindeki eklenti konaklarından bulunan uzantı noktalarından bulunan uzantı paketleri oluşturabilirsiniz:

![Eklenti mimarisi](media/extending-visual-studio-mac-addin1.png)

Bir uzantı paketinin Mac için Visual Studio derlemesi için, Mac için Visual Studio IDE içindeki önceden var olan uzantı noktalarından oluşturan uzantılara sahip olması gerekir. Bir uzantı paketi, eklenti konağında tanımlı bir uzantı noktasını temel aldığında, _dependency_   Bu uzantı paketine bağımlılığı vardır.

Bu modüler tasarımın avantajı Mac için Visual Studio Genişletilebilir olduğundan, özel uzantı paketleriyle birlikte derleyebilen birçok uzantı noktası vardır. Geçerli uzantı paketlerine örnek olarak C# ve F #, hata ayıklayıcı araçları ve proje şablonları için destek verilebilir.

> [!NOTE]
> Eklenti Oluşturucu 1,2 ' den önce oluşturulmuş bir eklenti Oluşturucu projeniz varsa, [Aşağıdaki adımlarda açıklandığı](https://mhut.ch/addinmaker/1.2)gibi projenizi geçirmeniz gerekir.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Bu bölüm, eklenti Oluşturucu tarafından oluşturulan farklı dosyalara ve bir komut uzantısının gerektirdiği verilere bakar.

## <a name="attribute-files"></a>Öznitelik dosyaları

Uzantı paketleri, C# özniteliklerinde ad, sürüm, bağımlılıklar ve diğer bilgilerle ilgili meta verileri depolar. Eklenti Oluşturucu, `AddinInfo.cs` `AssemblyInfo.cs` Bu bilgileri depolamak ve düzenlemek için iki dosya oluşturur. Uzantı paketleri, *eklenti özniteliğinde*belirtilen benzersiz bir kimliğe ve ad alanına sahip olmalıdır:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Uzantı paketleri, içinde çalıştıkları uzantı noktalarına sahip olan uzantı paketlerinde bağımlılıklar da bildirmelidir. Bunlar derleme zamanında otomatik olarak başvurulur.

Ayrıca, aşağıdaki görüntüde gösterildiği gibi, projenin çözüm panelindeki eklenti başvurusu düğümü aracılığıyla ek başvurular eklenebilir:

![Tarih Ekle ekran görüntüsü](media/extending-visual-studio-mac-addin13.png)

Ayrıca, derleme zamanında bunlara karşılık gelen `assembly:AddinDependency` öznitelikleri de eklenir. Meta veriler ve bağımlılık bildirimleri olduktan sonra, uzantı paketinin temel yapı taşlarına odaklanırsınız.

## <a name="extensions-and-extension-points"></a>Uzantılar ve uzantı noktaları

Uzantı noktası, bir veri yapısını (bir tür) tanımlayan bir yer tutucudur, ancak uzantı belirli bir uzantı noktası tarafından belirtilen yapıya uygun olan verileri tanımlar. Uzantı noktaları, bildiriminde kabul edebilecekleri uzantı türünü belirtir. Uzantılar, tür adları veya uzantı yolları kullanılarak bildirilmiştir. İhtiyaç duyduğunuz uzantı noktasının nasıl oluşturulacağı hakkında daha ayrıntılı bir açıklama için [uzantı noktası başvurusuna](https://github.com/mono/mono-addins/wiki/Extension-Points) bakın.

Uzantı/uzantı noktası mimarisi Mac için Visual Studio hızlı ve modüler geliştirmeyi korur.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Komut uzantıları

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Komut uzantıları, her yürütüldüğünde çağrılan yöntemlere işaret eden uzantılardır.

Komut uzantıları, uzantı noktasına girdi eklenerek tanımlanır `/MonoDevelop/Ide/Commands` . Şu kod ile uzantımızı tanımlıyoruz `Manifest.addin.xml` :

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Uzantı düğümü, bu durumda, içinde bulunduğu uzantı noktasını belirten bir yol özniteliği içerir `/MonoDevelop/Ide/Commands/Edit` . Ayrıca, komutuna bir üst düğüm işlevi görür. Komut düğümü aşağıdaki özniteliklere sahiptir:

* **ID** -bu komut için tanımlayıcıyı belirtir. Komut tanımlayıcıları, numaralandırma üyeleri olarak bildirilmelidir ve komutları Commandıtems 'lara 'e bağlamak için kullanılır.
* **_label** -menülerde gösterilecek metin.
* **_description** -araç çubuğu düğmeleri için araç ipucu olarak gösterilecek metin.
* **Defaulthandler** - `CommandHandler` komutu destekleyen sınıfı belirtir

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Uzantı noktasına takılan bir CommandItem uzantısı `/MonoDevelop/Ide/MainMenu/Edit` Aşağıdaki kod parçacığında gösterilmiştir:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem, ID özniteliğinde belirtilen bir komutu bir menüye koyar. Bu CommandItem `/MonoDevelop/Ide/MainMenu/Edit` , komut etiketinin **düzenleme menüsünde**görünmesini sağlayan uzantı noktasını genişletir. CommandItem içindeki **kimliğin** komut düğümünün kimliğine karşılık geldiğini unutmayın `InsertDate` . CommandItem öğesini kaldırdıysanız, **Ekle tarihi** seçeneği, düzenleme menüsünden kaybolur.

### <a name="command-handlers"></a>Komut Işleyicileri

, `InsertDateHandler` Sınıfının bir uzantısıdır `CommandHandler` . İki yöntemi geçersiz kılar `Update` ve `Run` . Bir `Update` komut bir menüde gösterildiğinde veya anahtar bağlamaları aracılığıyla yürütüldüğünde Yöntem sorgulanır. Bilgi nesnesini değiştirerek, komutu devre dışı bırakabilir veya görünmez yapabilir, dizi komutlarını doldurabilir ve daha fazlasını yapabilirsiniz. Bu `Update` Yöntem, içine metin eklemek için bir *TextEditor* Ile etkin bir *belge* bulamazsa komutu devre dışı bırakır:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Yalnızca `Update` komutu etkinleştirmek veya gizlemek için özel mantığınızı kullandığınızda yöntemi geçersiz kılmanız gerekir. Yöntemi, bir Kullanıcı bir `Run` komutu her çalıştırdığında yürütülür ve bu durumda Kullanıcı düzenleme menüsünden komutu seçtiğinde oluşur. Bu yöntem, metin düzenleyicisinde giriş işaretine tarih ve saat ekler:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Komut türünü, içinde bir numaralandırma üyesi olarak bildirin `DateInserterCommands` :

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Bu, komutu ve CommandItem komutunu birleştirerek, **Düzenle menüsünden**CommandItem seçildiğinde komutları çağırır.

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

## <a name="additional-information"></a>Ek Bilgi

> [!NOTE]
> Şu anda Mac için Visual Studio için genişletilebilirlik senaryolarını geliştirmeye çalışıyoruz. Uzantılar oluşturuyorsanız ve ek yardım veya bilgilere ihtiyacınız varsa veya geri bildirim sağlamak istiyorsanız, lütfen [Mac için Visual Studio uzantısı yazma](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u) formunu girin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio uzantıları geliştirme (Windows üzerinde)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
