---
title: Mac için Visual Studio’yu Genişletme
description: Mac'in özellikleri ve işlevselliği için Visual Studio, uzantı paketleri adı verilen modüllerle genişletilebilir. Bu kılavuzun ilk bölümü, tarih ve saati belgeye eklemek için Mac uzantı paketi için basit bir Visual Studio oluşturur. Bu kılavuzun ikinci bölümü, uzantılı paket sisteminin temellerini ve Mac için Visual Studio'nun temelini oluşturan bazı temel API'leri tanıtır.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 29c5bb9c45ae8d859316bd9c63eec10a6a425571
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75851965"
---
# <a name="extending-visual-studio-for-mac"></a>Mac için Visual Studio’yu Genişletme

Mac için Visual *Studio, Uzantı Paketleri*adı verilen bir dizi modülden oluşur. Ek bir dil desteği veya yeni bir Proje şablonu gibi Mac için Visual Studio'ya yeni işlevler tanıtmak için Uzantı Paketleri'ni kullanabilirsiniz.

Uzantı paketleri, diğer uzantı paketlerinin *uzantı* noktalarından oluşturur. Uzantı noktaları, menü veya IDE Komutları listesi gibi genişletilebilen alanlar için yer tutuculardır. Uzantı paketi, yeni bir menü öğesi veya yeni komut gibi uzantı adı verilen yapılandırılmış verilerin düğümlerini kaydederek bir uzantı noktasından oluşturabilir. Her uzantı noktası Komut, *Pad*veya *Command* *FileTemplate*gibi belirli türde uzantıları kabul eder. Diğer uzantı paketleri tarafından uzatılabildiği için, uzantı noktaları içeren bir modüle *eklenti ana bilgisayar*denir.

Mac için Visual Studio'yu özelleştirmek için, Aşağıdaki diyagramda gösterildiği gibi, Mac için Visual Studio'daki önceden varolan kitaplıklarda eklenti ana bilgisayarlarında bulunan uzantı noktalarından bir uzantı paketi oluşturabilirsiniz:

![Eklenti Mimarisi](media/extending-visual-studio-mac-addin1.png)

Mac için Visual Studio'dan bir uzantı paketi oluşturabilmesi için, Mac IDE için Visual Studio'da önceden varolan uzatma noktalarından inşa edilen uzantılara sahip olması gerekir. Bir uzantı paketi, eklenti ana bilgisayarda tanımlanan bir uzantı noktasına dayanıyorsa, bu uzantı paketine _bağımlı_ olduğu söylenir.

Bu modüler tasarımın yararı, Mac için Visual Studio'nun genişletilebilir olmasıdır - özel uzatma paketleri yle üzerine inşa edilebilen birçok uzatma noktası vardır. Geçerli uzantı paketlerine örnek olarak C# ve F#, hata ayıklama araçları ve Proje şablonları desteği verilebilir.

> [!NOTE]
> Eklenti Oluşturucu 1.2'den önce oluşturulmuş bir Eklenti Oluşturucu projeniz varsa, projenizi [buradaki](https://mhut.ch/addinmaker/1.2)adımlarda belirtildiği gibi geçirmeniz gerekir.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Bu bölümde, Eklenti Oluşturucu tarafından oluşturulan farklı dosyalar ve komut uzantısı için gereken veriler bak.

## <a name="attribute-files"></a>Öznitelik dosyaları

Uzantı paketleri, c# özniteliklerinde ad, sürüm, bağımlılıklar ve diğer bilgilerle ilgili meta verileri depolar. Eklenti Oluşturucu, bu bilgileri `AddinInfo.cs` `AssemblyInfo.cs` depolamak ve düzenlemek için iki dosya oluşturur. Uzantı paketleri, *Addin özyüründe*belirtilen benzersiz bir kimlik ve ad alanına sahip olmalıdır:

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

Uzantı paketleri, taktıkları uzantı noktalarına sahip olan uzantı paketlerine bağımlılıklar da bildirmelidir. Bunlar, yapı zamanında otomatik olarak başvurulur.

Ayrıca, proje için çözüm defterindeki Add-in referans düğümü aracılığıyla aşağıdaki resimde görüldüğü gibi ek başvurular eklenebilir:

![Tarih Ekran Ekle](media/extending-visual-studio-mac-addin13.png)

Ayrıca, ilgili `assembly:AddinDependency` öznitelikleri niyapı zamanında eklenir. Meta veriler ve bağımlılık bildirimleri yerleştirildikten sonra, uzantı paketinin temel yapı taşlarına odaklanabilirsiniz.

## <a name="extensions-and-extension-points"></a>Uzantılar ve uzantı noktaları

Uzantı noktası, bir veri yapısını (bir tür) tanımlayan bir yer tutucuiken, uzantı belirli bir uzantı noktası tarafından belirtilen bir yapıya uygun verileri tanımlar. Uzantı noktaları, beyannamelerinde ne tür bir uzantı kabul edebileceklerini belirtir. Uzantılar tür adları veya uzantı yolları kullanılarak bildirilir. İhtiyacınız olan uzantı noktasının nasıl oluşturulabildiğini hakkında daha ayrıntılı bir açıklama için [Uzantı Noktası başvurusuna](https://github.com/mono/mono-addins/wiki/Extension-Points) bakın.

Uzatma/uzatma noktası mimarisi, Mac için Visual Studio'nun gelişimini hızlı ve modüler tutar.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Komut Uzantıları

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Komut Uzantıları, her yürütüldünde çağrılan yöntemlere işaret eden uzantılardır.

Komut `/MonoDevelop/Ide/Commands` Uzantıları, uzantı noktasına girişler eklenerek tanımlanır. Uzantımızı aşağıdaki `Manifest.addin.xml` kodla tanımladık:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaulthandler="DateInserter.InsertDateHandler" />
</Extension>
```

Uzantı düğümü, bu durumda, `/MonoDevelop/Ide/Commands/Edit`takıldığında ki uzantı noktasını belirten bir yol özniteliği içerir. Ayrıca, Komutanlık için bir üst düğüm olarak hareket eder. Komut düğümü aşağıdaki özelliklere sahiptir:

* **id** - Bu Komutun tanımlayıcısını belirtir. Komut Tanımlayıcıları numaralandırma üyesi olarak bildirilmelidir ve Komutları CommandItems'a bağlamak için kullanılır.
* **_label** - Menülerde gösterilecek metin.
* **_description** - Araç çubuğu düğmeleri için araç ipucu olarak gösterilecek metin.
* **defaultHandler** - Komuta `CommandHandler` güç veren sınıfı belirtir

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

`/MonoDevelop/Ide/MainMenu/Edit` Uzantı noktasına takılan bir CommandItem uzantısı aşağıdaki kod snippet gösterilir:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <commanditem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem, kimlik özelliğinde belirtilen bir Komutu menüye yerleştirir. Bu CommandItem `/MonoDevelop/Ide/MainMenu/Edit` uzantı noktasını genişletiyor ve bu da Komutetiketinin **Edit Menüsünde**görünmesini sağlıyor. CommandItem'deki **kimliğin** Komut düğümünün kimliğine karşılık geldiğini `InsertDate`unutmayın. CommandItem'i kaldırırsanız, **Ekle Tarihi** seçeneği Menü'den kaybolur.

### <a name="command-handlers"></a>Komut Işleyicileri

Sınıfın `InsertDateHandler` bir uzantısıdır. `CommandHandler` İki yöntemi geçersiz `Update` kılar `Run`ve. Bir `Update` Komut bir menüde gösterildiğinde veya anahtar bağlamaları aracılığıyla yürütüldüğünde yöntem sorgulanır. Bilgi nesnesini değiştirerek Komutu devre dışı bırakıp görünmez hale getirebilir, dizi komutlarını doldurabilir ve daha fazlasını yapabilirsiniz. Bu `Update` yöntem, metin eklemek için *TextEditor* içeren etkin bir *Belge* bulamazsa komutu devre dışı kılabilir:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Yalnızca Komutu `Update` etkinleştirmek veya gizlemek için özel bir mantığınız olduğunda yöntemi geçersiz kılmanız gerekir. Yöntem, `Run` bir kullanıcı bir Komut yürütür, bu durumda bir kullanıcı Menü'den Komut'u seçtiğinde oluşur çalıştırın. Bu yöntem, metin düzenleyicisindeki basamaktaki tarih ve saati ekler:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Komut türünü numaralandırma üyesi olarak `DateInserterCommands`bildirin:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Bu, Command and CommandItem'i birbirine bağlar - **CommandItem, Edit Menüsünden**CommandItem seçildiğinde Komut Uyruğu çağırır.

## <a name="ide-apis"></a>IDE API'ler

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Geliştirme için kullanılabilen alanların kapsamı hakkında bilgi için [Uzantı Ağacı Başvurusu](https://www.monodevelop.com/developers/articles/extension-tree-reference/) ve [API Genel Bakış'a](https://www.monodevelop.com/developers/articles/api-overview/)bakın. Gelişmiş uzantı paketleri inşa ederken, [Geliştirici Makaleleri'ne](https://www.monodevelop.com/developers/articles/)de bakın. Aşağıda özelleştirme için alanların kısmi bir listesi verilmiştir:

* Pedleri
* Anahtar Bağlama Şemaları
* İlkeler
* Kod formatters
* Proje dosya biçimleri
* Tercih panelleri
* Seçenekler Panelleri
* Hata Ayıklama Protokolleri
* Hata ayıklayıcı görselleştiriciler
* Çalışma alanı düzenleri
* Çözüm pad ağaç düğümleri
* Kaynak düzenleyici kenar boşlukları
* Birim test motorları
* Kod jeneratörleri
* Kod parçacıkları
* Hedef çerçeveler
* Hedef çalışma süresi
* VCS arka uçları
* Yeniden Düzenle
* Yürütme işleyicileri
* Sözdizimi vurgulama

## <a name="additional-information"></a>Ek Bilgi

> [!NOTE]
> Şu anda Mac için Visual Studio için genişletilebilirlik senaryoları geliştirmek için çalışıyoruz. Uzantılar oluşturuyorsanız ve ek yardıma veya bilgiye ihtiyacınız varsa veya geri bildirim sağlamak istiyorsanız, lütfen [Mac Uzantılı Yazma](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u) formu için Visual Studio'yu doldurun.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio uzantıları geliştirme (Windows'ta)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
