---
title: Python kodunu düzenleme
description: Python için Visual Studio, biçimlendirme, linting ve refactoring'in yanı sıra zengin IntelliSense, kod parçacıkları ve navigasyon özellikleri sağlar.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: eb3e3ca5d18429c60894c42bda12328836dc6fc8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "73024731"
---
# <a name="edit-python-code"></a>Python kodunu düzenleme

Geliştirme zamanınızın çoğunu kod düzenleyicisinde geçirdiğiniz için Visual [Studio'daki Python desteği](installing-python-support-in-visual-studio.md) daha üretken olmanıza yardımcı olacak işlevsellik sağlar. Özellikler arasında IntelliSense sözdizimi vurgulama, otomatik tamamlama, imza yardımı, yöntem geçersiz kılma, arama ve gezinme bulunmaktadır.

Editör ayrıca Visual **Studio'daki Interactive** penceresi ile entegre edilmiştir ve bu da ikisi arasında kod alışverişini kolaylaştırır. Bkz. [Öğretici Adım 3: İnteraktif REPL penceresini kullanın](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) ve Etkileşimli pencereyi kullanın - Ayrıntılar için [İnteraktif komutuna gönder.](python-interactive-repl-in-visual-studio.md#send-to-interactive-command)

Visual Studio'da kod düzenleme yle ilgili genel belgeler için [kod düzenleyicisinin özelliklerine](../ide/writing-code-in-the-code-and-text-editor.md)bakın. Ayrıca [bkz.](../ide/outlining.md)

Her modülde tanımlanan Python sınıflarını ve bu sınıflarda tanımlanan işlevleri incelemek için Visual Studio **Object Browser** **(Diğer Windows** > **Nesne Tarayıcısını** **Görüntüle** > veya **Ctrl**+**W** > **J)** de kullanabilirsiniz.

## <a name="intellisense"></a>IntelliSense

IntelliSense [tamamlamaları](#completions)sağlar, [imza yardım,](#signature-help) [hızlı bilgi](#quick-info), ve kod [boyama](#code-coloring). Visual Studio 2017 sürümleri 15.7 ve daha sonra da [tip ipuçları](#type-hints)nı destekler.

Performansı artırmak için Visual Studio 2017 sürüm 15.5 ve daha önceki IntelliSense, projenizdeki her Python ortamı için oluşturulan bir tamamlama veritabanına bağlıdır. Paketleri eklerseniz, kaldırırsanız veya güncellerseniz veritabanlarının yenilenmesi gerekebilir. Veritabanı durumu, **IntelliSense** sekmesinde **Python Ortamları** penceresinde **(Çözüm Gezgini'nin**bir kardeşi) gösterilir [(Bkz. Ortamlar penceresi başvurusu).](python-environments-window-tab-reference.md)

Visual Studio 2017 sürüm 15.6 ve daha sonra veritabanına bağlı olmayan IntelliSense tamamlamaları sağlamak için farklı bir araç kullanır.

### <a name="completions"></a>Tamamlamalar

Tamamlamalar, düzenleyicideki geçerli konumda uygun şekilde girilebilecek ifadeler, tanımlayıcılar ve diğer sözcükler olarak görünür. Listede gösterilenler içeriğe bağlıdır ve yanlış veya dikkat dağıtıcı seçenekleri atlamak için filtrelenir. Tamamlamalar genellikle farklı ifadeler `import`(örneğin) ve işleçler (bir dönem dahil) yazarak tetiklenir, ancak **ctrl**+**J** > **Space**yazarak istediğiniz zaman görünmesini sağlayabilirsiniz.

![Visual Studio editöründe üye tamamlama](media/code-editing-completions-simple.png)

Bir tamamlama listesi açıldığında, ok tuşlarını, fareyi kullanarak veya yazmaya devam ederek istediğiniz tamamlamayı arayabilirsiniz. Siz daha fazla harf yazdıkça, liste olası tamamlanmaları göstermek için daha da filtrelenir. Ayrıca şu gibi kısayollar da kullanabilirsiniz:

- 'argparse' bulmak için 'ayrışma' gibi adın başında olmayan harfleri yazma
- 'AbstractBaseClass' veya 'air' gibi sözcüklerin başında ki harfleri yazmak 'as_integer_ratio'
- 'base64' bulmak için 'b64' gibi harfleri atlama

Bazı örnekler:

![Visual Studio editöründe filtreleme ile üye tamamlama](media/code-editing-completion-filtering.png)

Bir değişken veya değerden sonra bir dönem yazdığınızda üye tamamlanmaları, olası türlerin yöntemleri ve öznitelikleriyle birlikte otomatik olarak görüntülenir. Bir değişken birden fazla türe sahipse, liste her türlü tüm olasılıkları içerir ve hangi türlerin her tamamlamayı desteklediğini gösteren ek bilgiler içerir. Bir tamamlama tüm olası türler tarafından desteklenirse, ek açıklama olmadan gösterilir.

![Visual Studio editöründe birden fazla türde üye tamamlama](media/code-editing-completion-types.png)

Varsayılan olarak, "dunder" üyeleri (çift alt çizgiyle başlayan ve biten üyeler) gösterilmez. Genel olarak, bu tür üyelere doğrudan erişilmemelidir. Ancak, bir taneye ihtiyacınız varsa, önde gelen çift alt çizgiyi yazmak bu tamamlamaları listeye ekler:

![Visual Studio editöründe özel üye tamamlama](media/code-editing-completion-dunder.png)

Ve `import` `from ... import` deyimler içe aktarılabilen modüllerin listesini görüntüler. `from ... import`, liste belirtilen modülden içe aktarılabilir üyeleri içerir.

![Visual Studio editöründe alma işlemi tamamlama](media/code-editing-completion-import.png)

Ve `raise` `except` deyimler, hata türleri olma olasılığı yüksek olan sınıfların listelerini görüntüler. Liste, kullanıcı tarafından tanımlanan tüm özel durumları içermeyebilir, ancak uygun yerleşik özel durumları hızlı bir şekilde bulmanıza yardımcı olur:

![Visual Studio editöründe özel durum tamamlama](media/code-editing-completion-exception.png)

@ yazma bir dekoratör başlar ve potansiyel dekoratörler gösterir. Bu öğelerin çoğu dekoratör olarak kullanılabilir değildir; hangisini kullanacağımı belirlemek için kitaplık belgelerini kontrol edin.

![Visual Studio editöründe dekoratör tamamlama](media/code-editing-completion-decorator.png)

> [!Tip]
> Tamamlanma davranışını **Araçlar** > **Seçenekleri** > **Metin Düzenleyicisi** > **Python** > **Advanced**aracılığıyla yapılandırabilirsiniz. Bunlar arasında, **arama dizesini temel alan Filtre listesi,** siz yazarken tamamlama önerilerinin filtrelemi (varsayılan işaretlenir) uygular ve **Üye tamamlama görüntüler yalnızca** tüm olası türler tarafından desteklenen tamamlanmaları gösterir (varsayılan işaretlenmez). Bkz. [Seçenekler - tamamlanma sonuçları](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>İpuçları yazın

*Visual Studio 2017 sürüm 15.7 ve sonrası.*

Python 3.5+'daki "tür ipuçları"[(PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org), bağımsız değişken, iade değerleri ve sınıf öznitelikleritürlerini gösteren işlevler ve sınıflar için bir ek açıklama sözdizimidir. IntelliSense, işlev çağrıları, bağımsız değişkenler ve bu ek açıklamalara sahip değişkenlerin üzerinde gezinirken tür ipuçlarıgörüntüler.

Aşağıdaki örnekte, `Vector` sınıf `List[float]`olarak bildirilir ve `scale` işlev hem bağımsız değişkenleri hem de döndürme değeri için tür ipuçları içerir. Bu işleve yapılan bir çağrının üzerinde gezinmek tür ipuçlarını gösterir:

![Tür ipuçlarını ortaya çıkarmak için bir işlev çağrısı nın üzerinde gezinme](media/code-editing-type-hints1.png)

Aşağıdaki örnekte, `Employee` sınıfın açıklamalı özniteliklerinin bir öznitelik için IntelliSense tamamlama açılır açılır açılır penceresinde nasıl göründüğünü görebilirsiniz:

![IntelliSense tamamlama türü ipuçları gösteren](media/code-editing-type-hints2.png)

Projeniz boyunca tür ipuçlarını doğrulamak da yararlıdır, çünkü hatalar normalde çalışma süresine kadar görünmez. Bu amaçla Visual Studio, bağlam menüsü komutu **Python** > **Run Mypy** in **Solution Explorer**aracılığıyla endüstri standardı MyPy aracını entegre eder:

![Solution Explorer'da MyPy bağlam menüsü komutunu çalıştırın](media/code-editing-type-hints-run-mypy.png)

Komutu çalıştırmak, gerekirse mypy paketini yüklemenizi ister. Visual Studio daha sonra projedeki her Python dosyasındaki tür ipuçlarını doğrulamak için mypy'yi çalıştırır. Görsel Stüdyo Hata **Listesi** penceresinde hatalar görünür. Pencerede bir öğe seçmek, kodunuzdaki uygun satıra yönlendirin.

Basit bir örnek olarak, aşağıdaki işlev tanımı bağımsız `input` değişkenin `str`tür olduğunu belirten bir tür ipucu içerir, bu nedenleişlevin çağrısı bir tamsayı geçmeye çalışır:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Bu kodüzerinde **Mypy Çalıştır** komutunu kullanarak aşağıdaki hatayı oluşturur:

![Mypy doğrulama türü ipuçları örnek sonucu](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Python'un 3.5'ten önceki sürümleri için Visual Studio, Typeshed *saplama dosyaları* *(.pyi)* aracılığıyla sağladığınız tür ipuçlarını da görüntüler. Tür ipuçlarını doğrudan kodunuza eklemek istemediğinizde veya bunları doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğinizde saplama dosyalarını kullanabilirsiniz. Daha fazla bilgi için mypy project wiki'deki [Python modülleri için saplamalar oluştur](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) sayfasına bakın.
>
> Şu anda Visual Studio yorumlarda tür ipuçlarını desteklemiyor.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Python'un 3.5'ten önceki sürümleri için Visual Studio, Typeshed *saplama dosyaları* *(.pyi)* aracılığıyla sağladığınız tür ipuçlarını da görüntüler. Tür ipuçlarını doğrudan kodunuza eklemek istemediğinizde veya bunları doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğinizde saplama dosyalarını kullanabilirsiniz. Daha fazla bilgi için mypy project wiki'deki [Python modülleri için saplamalar oluştur](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) sayfasına bakın.
>
> Visual Studio, Python 2 ve 3 için Typeshed dosyaları kümesi ni içerir, bu nedenle ek indirmeler gerekmez. Ancak, farklı bir dosya kümesi kullanmak istiyorsanız, **Araçlar** > **Seçenekleri** > **Python** > Dil**Sunucusu** seçeneklerinde yolu belirtebilirsiniz. [Bkz. Seçenekler - Dil Sunucusu](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Şu anda Visual Studio yorumlarda tür ipuçlarını desteklemiyor.
::: moniker-end

### <a name="signature-help"></a>İmza yardımı

İşlev çağıran kod yazarken, açılışı `(` yazdığınızda ve kullanılabilir belgeleri ve parametre bilgilerini görüntülerken imza yardımı görüntülenir. **Ctrl**+**Shift**+**Space** ile bir işlev çağrısı içinde görünmesini de sağlayabilirsiniz. Görüntülenen bilgiler, işlevin kaynak kodundaki belgeleme dizelerine bağlıdır, ancak varsayılan değerleri içerir.

![Visual Studio editöründe imza yardımı](media/code-editing-signature-help.png)

> [!Tip]
> İmza yardımLarını devre dışı kullanabilirsiniz, **Araçlar** > **Seçenekleri** > **Metin Editörü** > **Python** > **Genel'e** gidin ve **İfade tamamlama** > **Parametre bilgilerini**temizleyin.

### <a name="quick-info"></a>Hızlı bilgi

Fare işaretçisini bir tanımlayıcının üzerine gezinen bir Hızlı Bilgi araç ipucu görüntüler. Tanımlayıcıya bağlı olarak, Hızlı Bilgi olası değerleri veya türleri, kullanılabilir belgeleri, iade türlerini ve tanım konumlarını görüntüleyebilir:

![Visual Studio editöründe hızlı bilgi](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kod boyama

Kod boyama, kod çözümlemesi ile renk değişkenleri, deyimler ve kodunuzun diğer bölümlerine kadar olan bilgileri kullanır. Örneğin, modüllere veya sınıflara atıfta bulunan değişkenler işlevlerden veya diğer değerlerden farklı bir renkte gösterilebilir ve parametre adları yerel veya genel değişkenlerden farklı bir renkte görünür. (Varsayılan olarak, işlevler kalın olarak gösterilmez):

![Visual Studio düzenleyicisinde kod ve sözdizimi boyama](media/code-editing-code-coloring.png)

Renkleri özelleştirmek için **Araçlar** > **Seçenekleri** > **Ortamı** > **Yazı Tipleri ve Renkleri'ne** gidin ve Görüntü **öğeleri** listesindeki **Python** girişlerini değiştirin:

![Visual Studio'da Yazı Tipleri ve Renkler seçenekleri](media/code-editing-customize-colors.png)

> [!Tip]
> Kod boyamadevre dışı kalmak **için, Tools** > **Options** > Metin**Düzenleyicisi** > **Text Editor** > Python**Advanced'e** gidin ve türe göre **Çeşitli Seçenekler** > **Renk adlarını**temizleyin. Bkz. [Seçenekler - Çeşitli seçenekler.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

## <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, kısayol yazıp **Tab**tuşuna basarak veya **Edit** > **IntelliSense** > **Insert Code Snippet** ve **Surround With** komutlarını kullanarak, **Python'u**seçerek ve ardından istediğiniz parçacığı seçerek dosyalarınıza eklenebilen kod parçalarıdır.

Örneğin, `class` sınıf tanımı ekleyen bir kod snippet için bir kısayol. Yazarken otomatik tamamlama listesinde görünen snippet'i `class`görürsünüz:

![Sınıf kısayolu için kod snippet](media/code-editing-code-snippet-class.png)

**Tab** tuşuna basıldığında sınıfın geri kalanını oluşturur. Daha **sonra, Sekme**ile vurgulanan alanlar arasında hareket ettirerek ad ve üsler listesinin üzerine yazabilirsiniz, ardından gövdeyi yazmaya başlamak için **Enter** tuşuna basın.

![Tamamlamanız için kod parçacığının alanları yla ilgili önemli noktalar](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Menü komutları

 > **IntelliSense** > **Ekle Kodu Snippet** menü komutunu edit kullandığınızda, önce **Python'u**seçin, sonra bir parçacık seçin: **Edit**

![Insert Code Snippet komutu ile bir kod parçacığı seçme](media/code-editing-code-snippet-insert.png)

IntelliSense**Surround Komutuyla** **Edit** > **IntelliSense** > Surround, benzer şekilde, metin düzenleyicisindeki geçerli seçimi seçilen bir yapısal öğenin içine yerleştirir. Örneğin, aşağıdaki gibi bir kod biraz vardı varsayalım:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Bu kodu seçmek ve **Surround Komutu ile** seçmek, kullanılabilir parçacıkların bir listesini görüntüler. Listeden **def** seçilmesi, seçili kodu işlev tanımına yerleştirir ve vurgulanan işlev adı ve bağımsız değişkenler arasında gezinmek için **Sekme** anahtarını kullanabilirsiniz:

![Kod parçacıkları için Surround komutunu kullanma](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Kullanılabilir parçacıkları inceleyin

 >  **Araçlar****Kodu Snippets Manager** menüsü komutunu kullanarak ve dil olarak **Python'u** seçerek açılan **Code Snippets Manager'da**kullanılabilir kod parçacıklarını görebilirsiniz:

![Visual Studio'da Kod Parçacıkları Yöneticisi](media/code-editing-code-snippets-manager.png)

Kendi parçacıklarınızı oluşturmak için [Bkz. Walkthrough: Bir kod parçacığı oluşturun.](../ide/walkthrough-creating-a-code-snippet.md)

Paylaşmak istediğiniz harika bir kod parçacığı yazarsanız, bir özde yayınlamaktan çekinmeyin ve [bize bildirin.](https://github.com/Microsoft/PTVS/issues) Biz Visual Studio gelecekteki sürümüne dahil etmek mümkün olabilir.

## <a name="navigate-your-code"></a>Kodunuzda gezinme

Visual Studio'daki Python desteği, kaynak kodun kullanılabildiği kitaplıklar da dahil olmak üzere kodunuzda hızla gezinmek için çeşitli araçlar sağlar: [gezinti çubuğu](#navigation-bar), [**Kullanıma Aç,**](#go-to-definition) [**Tüm**](#navigate-to)Başvuruları Bul ve Tüm [**Başvuruları Bul**](#find-all-references). Ayrıca Visual Studio [**Nesne Tarayıcısı**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)kullanabilirsiniz.

### <a name="navigation-bar"></a>Gezinti çubuğu

Gezinti çubuğu her düzenleyici penceresinin üst kısmında görüntülenir ve iki düzeyli bir tanım listesi içerir. Sol açılır, geçerli dosyada üst düzey sınıf ve işlev tanımlarını içerir; sağ açılır, solda gösterilen kapsamdaki tanımların listesini görüntüler. Editörde gezinirken, listeler geçerli bağlamınızı göstermek için güncellenir ve doğrudan atlamak için bu listelerden bir giriş de seçebilirsiniz.

![Visual Studio editöründe Navigasyon Çubuğu](media/code-editing-navigation-bar.png)

> [!Tip]
> Gezinti çubuğunu gizlemek için **Araçlar** > **Seçenekleri** > Metin**Düzenleyicisi** > **Text Editor** > Python**Genel'e** gidin ve **Ayarlar** > **Gezinti çubuğunu**temizleyin.

### <a name="go-to-definition"></a>Tanıma Git

**Tanım'a Git,** bir tanımlayıcının (işlev adı, sınıf veya değişken gibi) kullanımından tanımlandığı kaynak koduna hızla atlar. Bir tanımlayıcıyı sağ tıklayarak ve **Tanıma Git'i** seçerek veya bakıcıyı tanımlayıcıya yerleştirerek ve **F12**tuşuna basarak çağırırsınız. Kaynak kodun kullanılabilmesi koşuluyla, kodunuz ve dış kitaplıklarınızda çalışır. Kitaplık kaynak kodu kullanılamıyorsa, **Tanıma** Git `import` bir modül başvurusu için ilgili ifadeye atlar veya bir hata görüntüler.

![Visual Studio'da Tanım komutuna git](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Gezinme

 > **Git To** komutu **(Ctrl**+**,**) edin, editörde herhangi bir dize yazabileceğiniz ve kodunuzda bu dizeyi içeren bir işlev, sınıf veya değişken tanımlayan olası eşleşmeleri görebileceğiniz bir arama kutusu görüntülenir. **Edit** Bu özellik, **tanıma git** gibi, ancak bir tanımlayıcının kullanımını bulmak zorunda kalmadan benzer bir özellik sağlar.

Herhangi bir adı çift tıklatma veya ok tuşları ile seçerek ve **Enter**, bu tanımlayıcının tanımına doğru ilerler.

![Visual Studio'da Komutaya Git](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Tüm Başvuruları Bul

**Tüm Başvuruları Bul,** belirli bir tanımlayıcının içe alma lar ve atamalar da dahil olmak üzere hem tanımlandığını hem de kullanıldığını keşfetmenin yararlı bir yoludur. Bir tanımlayıcıyı sağ tıklayarak ve **Tüm Başvuruları Bul'u**seçerek veya bakıcıyı tanımlayıcıya yerleştirerek ve **Shift**+**F12**tuşuna basarak çağırırsınız. Listedeki bir öğeyi çift tıklatmak, konumuna doğru ilerlerken.

![Tüm Referansları Bul sonuçları](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme](formatting-python-code.md)
- [Yeniden Düzenle](refactoring-python-code.md)
- [Linter kullanın](linting-python-code.md)
