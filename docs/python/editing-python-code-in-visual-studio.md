---
title: Python kodunu düzenleme
description: Python için Visual Studio, biçimlendirme, kodlama ve yeniden düzenleme yanında zengin IntelliSense, kod parçacıkları ve gezinti özellikleri sağlar.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73024731"
---
# <a name="edit-python-code"></a>Python kodunu düzenleme

Geliştirme zamanınızın çoğunu kod düzenleyicisinde harcaymanız nedeniyle, [Visual Studio 'Da Python desteği](installing-python-support-in-visual-studio.md) daha üretken olmanıza yardımcı olacak işlevselliği sağlar. Özellikler IntelliSense sözdizimi vurgulaması, otomatik tamamlama, imza yardımı, metot geçersiz kılmaları, arama ve gezinme içerir.

Düzenleyici Ayrıca Visual Studio 'daki **etkileşimli** pencereyle tümleşiktir ve bu iki arasında kod alışverişi kolaylaştırır. Ayrıntılar için bkz. [Adım 3: ETKILEŞIMLI REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) ve etkileşimli [pencereyi etkileşimli Gönder komutunu kullanma](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) .

Visual Studio 'da kod düzenleme hakkında genel belgeler için bkz. [kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md). Ayrıca, kodunuzun belirli bölümlerine odaklanmanıza yardımcı olan [anahat oluşturma](../ide/outlining.md)bölümüne bakın.

**Object Browser** **View**  >  **Other Windows**  >  **Object Browser** **Ctrl** + **W**  >  Her modülde tanımlanan Python sınıflarını ve bu sınıflarda tanımlanan işlevleri incelemek için Visual Studio nesne tarayıcısı (diğer Windows nesne tarayıcısı veya CTRL W**J**'yi görüntüle) da kullanabilirsiniz.

## <a name="intellisense"></a>IntelliSense

IntelliSense, [tamamlama](#completions), [imza yardımı](#signature-help), [hızlı bilgi](#quick-info)ve [kod renklendirme](#code-coloring)sağlar. Visual Studio 2017 sürümleri 15,7 ve üzeri de [tür ipuçlarını](#type-hints)destekler.

Performansı artırmak için, Visual Studio 2017 sürüm 15,5 ve önceki sürümlerde IntelliSense, projenizdeki her Python ortamı için oluşturulan bir tamamlanma veritabanına bağımlıdır. Paketleri ekler, kaldırırsanız veya güncelleştirirseniz veritabanlarının yenilenmesi gerekebilir. Veritabanı durumu, **IntelliSense** sekmesindeki **Python ortamları** penceresinde ( **Çözüm Gezgini**eşdüzey öğesi) gösterilir (bkz. [ortamlar pencere başvurusu](python-environments-window-tab-reference.md)).

Visual Studio 2017 sürüm 15,6 ve üzeri, veritabanına bağımlı olmayan IntelliSense tamamlamalar sağlamak için farklı bir yol kullanır.

### <a name="completions"></a>Tamamlamalar

Tamamlama deyimleri, tanımlayıcıları ve düzenleyicideki geçerli konuma uygun şekilde girilmiş olabilecek diğer sözcükler olarak görünür. Listede gösterilen Özellikler bağlam tabanlıdır ve yanlış veya dikkat dağıtıcı seçeneklerini atlamak üzere filtrelenmiştir. Tamamlamalar genellikle farklı deyimler (örneğin `import` ,) ve işleçler (bir nokta dahil) yazılarak tetiklenir, ancak **CTRL** + **J**  >  **Space**yazarak istediğiniz zaman görünmesini sağlayabilirsiniz.

![Visual Studio düzenleyicisinde üye Tamamlama](media/code-editing-completions-simple.png)

Bir tamamlanma listesi açıkken, ok tuşlarını, fareyi veya yazmaya devam ederek istediğiniz tamamlamayı arayabilirsiniz. Daha fazla harf yazdığınızda, liste muhtemelen tamamlanmaları göstermek için daha fazla filtrelenmiştir. Ayrıca, gibi kısayollar da kullanabilirsiniz:

- Adın başlangıcında olmayan, ' argparse ' bulmak için ' Parse ' gibi harfler yazma
- ' As_integer_ratio ' bulmak için ' soyut Ctbaseclass ' veya ' Air ' bulmak üzere sözcüklerin başlangıcında olan ' abc ' gibi yalnızca harfleri yazmak
- ' Base64 ' bulmak için ' B64 ' gibi harfler atlanıyor

Bazı örnekler:

![Visual Studio düzenleyicisinde filtrelemeye sahip üye Tamamlama](media/code-editing-completion-filtering.png)

Bir değişken veya değerden sonra bir nokta yazdığınızda, olası türlerin yöntemleri ve öznitelikleri ile birlikte tamamlama işlemleri otomatik olarak görünür. Bir değişken birden fazla türden ise, her bir tamamlamayı hangi türlerin desteklediğini belirtmek üzere ek bilgiler içeren tüm türlerden tüm olanaklar de bu listede bulunur. Tamamlanma tüm olası türler tarafından desteklendiğinde, ek açıklama olmadan gösterilir.

![Visual Studio Düzenleyicisi 'nde birden çok türden üye Tamamlama](media/code-editing-completion-types.png)

Varsayılan olarak, "din" üyeleri (çift alt çizgiyle başlayan ve biten Üyeler gösterilmez). Genel olarak, bu tür üyelere doğrudan erişilmemelidir. Ancak, bir tane gerekliyse, önde gelen çift alt çizgi yazılması bu tamamlanmaları listeye ekler:

![Visual Studio düzenleyicisinde özel üye Tamamlama](media/code-editing-completion-dunder.png)

`import`Ve `from ... import` deyimleri, içeri aktarılabilecek modüllerin bir listesini görüntüler. İle `from ... import` liste, belirtilen modülden içeri aktarılabilecek üyeleri içerir.

![Visual Studio Düzenleyicisi 'nde içeri aktarma tamamlama](media/code-editing-completion-import.png)

`raise`Ve `except` deyimleri, muhtemelen hata türleri olabilecek sınıfların listesini görüntüler. Liste, Kullanıcı tanımlı tüm özel durumları içermeyebilir, ancak uygun yerleşik özel durumları hızla bulmanıza yardımcı olur:

![Visual Studio düzenleyicisinde özel durum tamamlama](media/code-editing-completion-exception.png)

Yazma @ bir dekoratör başlatır ve potansiyel dekoratörler gösterir. Bu öğelerin birçoğu dekoratörler olarak kullanılamaz; hangisini kullanacağınızı öğrenmek için kitaplık belgelerini denetleyin.

![Visual Studio Düzenleyicisi 'nde dekoratör tamamlama](media/code-editing-completion-decorator.png)

> [!Tip]
> **Araç**  >  **seçenekleri**  >  **metin Düzenleyicisi**  >  **Python**  >  **Gelişmiş**aracılığıyla tamamlama davranışını yapılandırabilirsiniz. Bunlar arasında, **arama dizesini temel alan filtre listesi** , siz yazarken (varsayılan olarak işaretlidir) tamamlama önerilerinin filtrelemesini uygular ve **üye tamamlama, üyelerin kesişimini** yalnızca tüm olası türler tarafından desteklenen işlemleri gösterir (varsayılan olarak işaretli değildir). Bkz. [Seçenekler-tamamlanma sonuçları](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Tür ipuçları

*Visual Studio 2017 sürüm 15,7 ve üzeri.*

Python 3.5 + ' da "tür ipuçları" ([Pep 484](https://www.python.org/dev/peps/pep-0484/) (Python.org), bağımsız değişkenlerin türlerini, dönüş değerlerini ve sınıf özniteliklerini belirten işlevler ve sınıflar için ek açıklama sözdizimidir. IntelliSense, işlev çağrılarının, bağımsız değişkenlerin ve bu ek açıklamaların bulunduğu değişkenlerin üzerine geldiğinizde tür ipuçlarını görüntüler.

Aşağıdaki örnekte, `Vector` sınıfının olarak bildirildiği `List[float]` ve `scale` işlevi hem bağımsız değişkenleri hem de dönüş değeri için tür ipuçları içerir. Bu işleve yapılan bir çağrının üzerine gelindiğinde tür ipuçları gösterilmektedir:

![Tür ipuçlarını açığa çıkarmak için bir işlev çağrısının üzerine gelindiğinde](media/code-editing-type-hints1.png)

Aşağıdaki örnekte, sınıfının açıklamalı özniteliklerinin `Employee` bir öznitelik Için IntelliSense tamamlanma açılan penceresinde nasıl göründüğünü görebilirsiniz:

![IntelliSense tamamlanmasında tür ipuçları gösteriliyor](media/code-editing-type-hints2.png)

Genellikle çalışma zamanına kadar hatalar görünmeyeceği için, projenizin tamamında tür ipuçlarını doğrulamak da yararlıdır. Bu amaçla, Visual Studio, sektör standardı mypy aracını bağlam **menüsü komutu ile**tümleştirerek  >  **Çözüm Gezgini**' de**mypy 'yi çalıştırın** :

![Çözüm Gezgini MyPy bağlam menüsü komutunu çalıştırın](media/code-editing-type-hints-run-mypy.png)

Komutu çalıştırmak, gerekirse mypy paketini yüklemenizi ister. Ardından Visual Studio, projedeki her Python dosyasındaki tür ipuçlarını doğrulamak için mypy 'yi çalıştırır. Hatalar Visual Studio **hata listesi** penceresinde görüntülenir. Penceredeki bir öğenin seçilmesi kodunuzda uygun satıra gider.

Basit bir örnek olarak, aşağıdaki işlev tanımı bağımsız değişkenin tür olduğunu göstermek için bir tür ipucu içerir `input` `str` , ancak bu işleve yapılan çağrı bir tamsayı geçirmeye çalışır:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Bu kodda **Mypy Run** komutunu kullanmak aşağıdaki hatayı üretir:

![Mypy doğrulaması tür ipuçlarının örnek sonucu](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> 3,5 ' dan önceki Python sürümleri için, Visual Studio aynı zamanda, yazı tipinde bulunan *saplama dosyaları* (*. Pyi*) aracılığıyla sağladığınız tür ipuçlarını da görüntüler. Doğrudan kodunuzda tür ipuçlarını dahil etmek istediğinizde veya doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğinizde, saplama dosyalarını kullanabilirsiniz. Daha fazla bilgi için bkz. mypy proje wiki 'de [Python modülleri için saplamalar oluşturma](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) .
>
> Mevcut olduğunda Visual Studio, açıklamalarda tür ipuçlarını desteklemez.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> 3,5 ' dan önceki Python sürümleri için, Visual Studio aynı zamanda, yazı tipinde bulunan *saplama dosyaları* (*. Pyi*) aracılığıyla sağladığınız tür ipuçlarını da görüntüler. Doğrudan kodunuzda tür ipuçlarını dahil etmek istediğinizde veya doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğinizde, saplama dosyalarını kullanabilirsiniz. Daha fazla bilgi için bkz. mypy proje wiki 'de [Python modülleri için saplamalar oluşturma](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) .
>
> Visual Studio, Python 2 ve 3 için bir dizi yazı dosyası kümesi içerir, bu nedenle ek indirmeler gerekli değildir. Ancak, farklı bir dosya kümesi kullanmak istiyorsanız, **Araçlar**  >  **Seçenekler**  >  **Python**  >  **dil sunucusu** seçeneklerinde yolu belirtebilirsiniz. Bkz. [Seçenekler-dil sunucusu](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Mevcut olduğunda Visual Studio, açıklamalarda tür ipuçlarını desteklemez.
::: moniker-end

### <a name="signature-help"></a>İmza yardımı

Bir işlevi çağıran kodu yazarken, açma 'yı yazdığınızda imza yardımı görünür `(` ve kullanılabilir belgeleri ve parametre bilgilerini görüntüler. Ayrıca, **Ctrl** + **Shift** + bir işlev çağrısının içinde CTRL vardiyası**alanıyla** görünmesini sağlayabilirsiniz. Görünen bilgiler, işlevin kaynak kodundaki belge dizelerine bağlıdır, ancak varsayılan değerleri içerir.

![Visual Studio düzenleyicisinde imza yardımı](media/code-editing-signature-help.png)

> [!Tip]
> İmza yardımını devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Python**  >  **genel** ' e gidin ve **ekstre tamamlama**  >  **parametresi bilgilerini**temizleyin.

### <a name="quick-info"></a>Hızlı bilgi

Bir tanımlayıcı üzerinde fare işaretçisinin üzerine gelindiğinde bir Hızlı Bilgi ipucu görüntülenir. Tanımlayıcıya bağlı olarak hızlı bilgi, olası değerler veya türler, kullanılabilir tüm belgeler, dönüş türleri ve tanım konumları gösterebilir:

![Visual Studio düzenleyicisinde hızlı bilgi](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kod renklendirme

Kod renklendirme kod analizinden renk değişkenlerine, deyimlerine ve kodunuzun diğer bölümlerine kadar bilgi kullanır. Örneğin, modüller veya sınıflara başvuran değişkenler, işlevlerden veya diğer değerlerden farklı bir renkte görünebilir ve parametre adları yerel veya genel değişkenlerden farklı bir renkle gösterilir. (Varsayılan olarak işlevler kalın olarak gösterilmez):

![Visual Studio düzenleyicisinde kod ve söz dizimi renklendirmesi](media/code-editing-code-coloring.png)

Renkleri özelleştirmek için, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **yazı tipleri ve renkler** ' e gidin ve **görüntüleme öğeleri** listesinde **Python** girdilerini değiştirin:

![Visual Studio 'da yazı tipleri ve renkler seçenekleri](media/code-editing-customize-colors.png)

> [!Tip]
> Kod renklendirmesini devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Python**  >  **Gelişmiş** ' e gidin ve türe göre **çeşitli seçenekler**  >  **renk adlarını**temizleyin. Bkz. [Seçenekler-çeşitli seçenekler](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, bir kısayol yazıp **Tab**tuşuna basarak veya IntelliSense **düzenleme**  >  **IntelliSense**  >  **kodu kod parçacığını** ve komutlarla **çevrelemeyi** , **Python**'u seçip istenen kod parçacığını seçerek dosyalarınıza eklenebilen kod parçacıklarında yer alabilir.

Örneğin, bir `class` sınıf tanımı ekleyen kod parçacığına yönelik bir kısayoldur. Kod parçacığının, şunu yazdığınızda otomatik tamamlama listesinde göründüğünü görürsünüz `class` :

![Sınıf kısayolu için kod parçacığı](media/code-editing-code-snippet-class.png)

**Tab** tuşuna basıldığında sınıfın geri kalanı oluşturulur. Daha sonra ad ve temellerin listesini yazabilir, vurgulanan alanlar arasında **sekme**ile hareket edebilir ve ardından gövde yazmaya başlamak için **ENTER** tuşuna basabilirsiniz.

![Doldurmanız için bir kod parçacığı alanlarının üzerinde vurgular](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Menü komutları

IntelliSense 'i **Düzenle**  >  **IntelliSense**  >  **kod parçacığı Ekle** menü komutunu kullandığınızda, önce **Python**' ı, sonra da bir kod parçacığını seçin:

![Kod parçacığı Ekle komutuyla kod parçacığı seçme](media/code-editing-code-snippet-insert.png)

**Edit**  >  **IntelliSense**  >  Benzer şekilde IntelliSense**ile çevreleyin** komutu, geçerli seçimi seçili yapısal öğenin içine metin düzenleyicisine koyar. Örneğin, aşağıdaki gibi bir kod biraz daha olduğunu varsayalım:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Bu kodun seçilmesi ve **birlikte surround** komutuyla seçilmesi, kullanılabilir kod parçacıklarının bir listesini görüntüler. Listeden **def** seçilmesi, seçilen kodu bir işlev tanımına koyar ve vurgulanan işlev adı ile bağımsız değişkenler arasında gezinmek için **Tab** tuşunu kullanabilirsiniz:

![Kod parçacıkları için WITH komutuyla surround kullanma](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Kullanılabilir parçacıkları İncele

Kullanılabilir kod parçacıklarını, **Araçlar**kod parçacıkları Yöneticisi menü komutu kullanılarak açılan ve dil olarak Python seçeneğini belirleyerek **kod parçacıkları yöneticisinde**görebilirsiniz  >  **Code Snippets Manager** **Python** :

![Visual Studio 'da kod parçacıkları Yöneticisi](media/code-editing-code-snippets-manager.png)

Kendi kod parçacıklarınızı oluşturmak için bkz. [Izlenecek yol: kod parçacığı oluşturma](../ide/walkthrough-creating-a-code-snippet.md).

Paylaşmak istediğiniz harika bir kod parçacığı yazarsanız, bunu bir GİST içinde göndermekten ve [bize bildirelim](https://github.com/Microsoft/PTVS/issues). Bunu, Visual Studio 'nun gelecek bir sürümüne dahil edebiliriz.

## <a name="navigate-your-code"></a>Kodunuzda gezinme

Visual Studio 'da Python desteği, kodunuzun içinde, kaynak kodu kullanılabilir olan kitaplıklar da dahil olmak üzere çeşitli araçlar sağlar: [Gezinti çubuğu](#navigation-bar), [**Tanıma Git**](#go-to-definition), [**Gidilecek**](#navigate-to)ve [**tüm başvuruları bul**](#find-all-references). Visual Studio [**nesne tarayıcısı**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)de kullanabilirsiniz.

### <a name="navigation-bar"></a>Gezinti çubuğu

Gezinti çubuğu her bir düzenleyici penceresinin üst kısmında görüntülenir ve iki düzeyli bir tanım listesi içerir. Sol açılan liste, geçerli dosyadaki en üst düzey sınıfı ve işlev tanımlarını içerir; Sağ açılan listede, sol tarafta gösterilen kapsam içindeki tanımların bir listesi görüntülenir. Düzenleyicide hareket ettirmek için, listeler geçerli bağlamınızı gösterecek şekilde güncelleştirir ve bu listelerden doğrudan gitmek için bir giriş de seçebilirsiniz.

![Visual Studio düzenleyicisinde gezinti çubuğu](media/code-editing-navigation-bar.png)

> [!Tip]
> Gezinti çubuğunu gizlemek için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Python**  >  **genel** ve açık **Ayarlar**  >  **Gezinti çubuğu**' na gidin.

### <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git** , bir tanımlayıcının (bir işlev adı, sınıf veya değişken) tanımlandıkları kaynak koda hızlı bir şekilde atlanacaktır. Bir tanımlayıcıya sağ tıklayıp **Tanıma Git** ' i seçerek ve giriş işaretini tanımlayıcıya yerleştirip **F12**tuşuna basarak bu seçeneği çağırın. Bu, kodunuz ve harici kitaplıklarınızda çalışarak kaynak kodunun kullanılabilir olmasını sağladı. Kitaplık kaynak kodu kullanılabilir değilse, **tanım** ' `import` a bir modül başvurusu için ilgili ifadeye atlar veya bir hata görüntüler.

![Visual Studio 'da tanıma komutuna git](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Şuraya gidin

**Edit**  >  **Git** komutuna Düzenle (**CTRL** + **,**), düzenleyicide herhangi bir dize yazabileceğiniz ve kodunuzda, sınıfta veya bu dizeyi içeren değişkeni tanımlayan olası eşleşmeleri görebileceğiniz bir arama kutusu görüntüler. Bu özellik, **Tanıma Git** , ancak tanımlayıcı kullanımını bulmaya gerek kalmadan, benzer bir yetenek sağlar.

Herhangi bir ada çift tıklayın veya ok tuşlarıyla ve **ENTER**ile seçip, Bu tanımlayıcının tanımına gider.

![Visual Studio 'da komuta git](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Tüm Başvuruları Bul

**Tüm başvuruları bul** , içeri aktarmalar ve atamalar dahil olmak üzere, verilen her bir tanımlayıcının hem tanımlanmış hem de kullanıldığı yerleri bulmanın yararlı bir yoludur. Bir tanımlayıcıya sağ tıklayıp **tüm başvuruları bul**' u seçerek veya giriş işaretini tanımlayıcıya yerleştirip **SHIFT** + **F12**tuşlarına basarak çağırabilirsiniz. Listedeki bir öğeye çift tıklamak, konumuna gider.

![Tüm başvuruları bul sonuçları](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme](formatting-python-code.md)
- [Yeniden Düzenle](refactoring-python-code.md)
- [Bir Inter kullanın](linting-python-code.md)
