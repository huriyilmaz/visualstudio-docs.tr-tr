---
title: Python kodunu düzenleme
description: Python için Visual Studio, biçimlendirme, kodlama ve yeniden düzenleme özellikleriyle zengin ıntellisense, kod parçacıkları ve gezinti özellikleri sağlar.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 1ba70337e5ac7ae511fefa609c73b0efba414152
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126628322"
---
# <a name="edit-python-code"></a>Python kodunu düzenleme

geliştirme zamanınızın çoğunu kod düzenleyicisinde harcaymanız nedeniyle [Visual Studio 'de Python desteği](installing-python-support-in-visual-studio.md) daha üretken olmanıza yardımcı olacak işlevselliği sağlar. Özellikler IntelliSense sözdizimi vurgulaması, otomatik tamamlama, imza yardımı, metot geçersiz kılmaları, arama ve gezinme içerir.

düzenleyici ayrıca Visual Studio **etkileşimli** penceresiyle tümleşiktir ve bu iki arasında kod alışverişi kolaylaştırır. Ayrıntılar için bkz. [Adım 3: ETKILEŞIMLI REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) ve etkileşimli [pencereyi etkileşimli Gönder komutunu kullanma](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) .

Visual Studio kodu düzenleme hakkında genel belgeler için bkz. [kod düzenleyicisinin özellikleri](../ide/writing-code-in-the-code-and-text-editor.md). Ayrıca, kodunuzun belirli bölümlerine odaklanmanıza yardımcı olan [anahat oluşturma](../ide/outlining.md)bölümüne bakın.

   >    >    +   >  her modülde tanımlanan Python sınıflarını ve bu sınıflarda tanımlanan işlevleri incelemek için Visual Studio Nesne Tarayıcısı (diğer Windows Nesne Tarayıcısı veya Ctrl W **J**) de kullanabilirsiniz.

## <a name="intellisense"></a>IntelliSense

IntelliSense, [tamamlama](#completions), [imza yardımı](#signature-help), [hızlı bilgi](#quick-info)ve [kod renklendirme](#code-coloring)sağlar. Visual Studio 2017 sürümleri 15,7 ve üzeri de [tür ipuçlarını](#type-hints)destekler.

performansı artırmak için, Visual Studio 2017 sürüm 15,5 ve önceki sürümlerde ıntellisense, projenizdeki her Python ortamı için oluşturulan bir tamamlanma veritabanına bağlıdır. Paketleri ekler, kaldırırsanız veya güncelleştirirseniz veritabanlarının yenilenmesi gerekebilir. Veritabanı durumu, **IntelliSense** sekmesindeki **Python ortamları** penceresinde ( **Çözüm Gezgini** eşdüzey öğesi) gösterilir (bkz. [ortamlar pencere başvurusu](python-environments-window-tab-reference.md)).

Visual Studio 2017 sürüm 15,6 ve üzeri, veritabanına bağımlı olmayan ıntellisense tamamlamalar sağlamak için farklı bir yol kullanır.

### <a name="completions"></a>Tamamlamalar

Tamamlama deyimleri, tanımlayıcıları ve düzenleyicideki geçerli konuma uygun şekilde girilmiş olabilecek diğer sözcükler olarak görünür. Listede gösterilen Özellikler bağlam tabanlıdır ve yanlış veya dikkat dağıtıcı seçeneklerini atlamak üzere filtrelenmiştir. Tamamlamalar genellikle farklı deyimler (örneğin `import` ,) ve işleçler (bir nokta dahil) yazılarak tetiklenir, ancak **CTRL** + **J**  >  **Space** yazarak istediğiniz zaman görünmesini sağlayabilirsiniz.

![Visual Studio düzenleyicisinde üye tamamlama](media/code-editing-completions-simple.png)

Bir tamamlanma listesi açıkken, ok tuşlarını, fareyi veya yazmaya devam ederek istediğiniz tamamlamayı arayabilirsiniz. Daha fazla harf yazdığınızda, liste muhtemelen tamamlanmaları göstermek için daha fazla filtrelenmiştir. Ayrıca, gibi kısayollar da kullanabilirsiniz:

- Adın başlangıcında olmayan, ' argparse ' bulmak için ' Parse ' gibi harfler yazma
- ' As_integer_ratio ' bulmak için ' soyut Ctbaseclass ' veya ' Air ' bulmak üzere sözcüklerin başlangıcında olan ' abc ' gibi yalnızca harfleri yazmak
- ' Base64 ' bulmak için ' B64 ' gibi harfler atlanıyor

Bazı örnekler:

![Visual Studio düzenleyicisinde filtrelemeye sahip üye tamamlama](media/code-editing-completion-filtering.png)

Bir değişken veya değerden sonra bir nokta yazdığınızda, olası türlerin yöntemleri ve öznitelikleri ile birlikte tamamlama işlemleri otomatik olarak görünür. Bir değişken birden fazla türden ise, her bir tamamlamayı hangi türlerin desteklediğini belirtmek üzere ek bilgiler içeren tüm türlerden tüm olanaklar de bu listede bulunur. Tamamlanma tüm olası türler tarafından desteklendiğinde, ek açıklama olmadan gösterilir.

![Visual Studio düzenleyicisinde birden çok türden üye tamamlama](media/code-editing-completion-types.png)

Varsayılan olarak, "din" üyeleri (çift alt çizgiyle başlayan ve biten Üyeler gösterilmez). Genel olarak, bu tür üyelere doğrudan erişilmemelidir. Ancak, bir tane gerekliyse, önde gelen çift alt çizgi yazılması bu tamamlanmaları listeye ekler:

![Visual Studio düzenleyicisinde özel üye tamamlama](media/code-editing-completion-dunder.png)

`import`Ve `from ... import` deyimleri, içeri aktarılabilecek modüllerin bir listesini görüntüler. İle `from ... import` liste, belirtilen modülden içeri aktarılabilecek üyeleri içerir.

![Visual Studio düzenleyicisinde içeri aktarma tamamlama](media/code-editing-completion-import.png)

`raise`Ve `except` deyimleri, muhtemelen hata türleri olabilecek sınıfların listesini görüntüler. Liste, Kullanıcı tanımlı tüm özel durumları içermeyebilir, ancak uygun yerleşik özel durumları hızla bulmanıza yardımcı olur:

![Visual Studio düzenleyicisinde özel durum tamamlama](media/code-editing-completion-exception.png)

Yazma @ bir dekoratör başlatır ve potansiyel dekoratörler gösterir. Bu öğelerin birçoğu dekoratörler olarak kullanılamaz; hangisini kullanacağınızı öğrenmek için kitaplık belgelerini denetleyin.

![Visual Studio düzenleyicisinde dekoratör tamamlama](media/code-editing-completion-decorator.png)

> [!Tip]
> **Araç**  >  **seçenekleri**  >  **metin Düzenleyicisi**  >  **Python**  >  **Gelişmiş** aracılığıyla tamamlama davranışını yapılandırabilirsiniz. Bunlar arasında, **arama dizesini temel alan filtre listesi** , siz yazarken (varsayılan olarak işaretlidir) tamamlama önerilerinin filtrelemesini uygular ve **üye tamamlama, üyelerin kesişimini** yalnızca tüm olası türler tarafından desteklenen işlemleri gösterir (varsayılan olarak işaretli değildir). Bkz. [Seçenekler-tamamlanma sonuçları](python-support-options-and-settings-in-visual-studio.md#completion-results).

### <a name="type-hints"></a>Tür ipuçları

*Visual Studio 2017 sürüm 15,7 ve üzeri.*

Python 3.5 + ' da "tür ipuçları" ([Pep 484](https://www.python.org/dev/peps/pep-0484/) (Python.org), bağımsız değişkenlerin türlerini, dönüş değerlerini ve sınıf özniteliklerini belirten işlevler ve sınıflar için ek açıklama sözdizimidir. IntelliSense, işlev çağrılarının, bağımsız değişkenlerin ve bu ek açıklamaların bulunduğu değişkenlerin üzerine geldiğinizde tür ipuçlarını görüntüler.

Aşağıdaki örnekte, `Vector` sınıfının olarak bildirildiği `List[float]` ve `scale` işlevi hem bağımsız değişkenleri hem de dönüş değeri için tür ipuçları içerir. Bu işleve yapılan bir çağrının üzerine gelindiğinde tür ipuçları gösterilmektedir:

![Tür ipuçlarını açığa çıkarmak için bir işlev çağrısının üzerine gelindiğinde](media/code-editing-type-hints1.png)

Aşağıdaki örnekte, sınıfının açıklamalı özniteliklerinin `Employee` bir öznitelik Için IntelliSense tamamlanma açılan penceresinde nasıl göründüğünü görebilirsiniz:

![IntelliSense tamamlanmasında tür ipuçları gösteriliyor](media/code-editing-type-hints2.png)

Genellikle çalışma zamanına kadar hatalar görünmeyeceği için, projenizin tamamında tür ipuçlarını doğrulamak da yararlıdır. bu amaçla, Visual Studio sektör standart mypy aracını bağlam **menüsü komutu ile** tümleştirerek,  >  **Çözüm Gezgini** içinde **mypy çalıştırma** :

![Çözüm Gezgini MyPy bağlam menüsü komutunu çalıştırın](media/code-editing-type-hints-run-mypy.png)

Komutu çalıştırmak, gerekirse mypy paketini yüklemenizi ister. Visual Studio sonra, projedeki her Python dosyasındaki tür ipuçlarını doğrulamak için mypy ' yi çalıştırır. hatalar Visual Studio **Hata Listesi** penceresinde görünür. Penceredeki bir öğenin seçilmesi kodunuzda uygun satıra gider.

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
> Python 'un 3,5 öncesindeki sürümleri için Visual Studio, ayrıca, yazı türü olan *saplama dosyaları* (*. pyi*) aracılığıyla sağladığınız tür ipuçlarını da görüntüler. Doğrudan kodunuzda tür ipuçlarını dahil etmek istediğinizde veya doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğinizde, saplama dosyalarını kullanabilirsiniz. Daha fazla bilgi için bkz. mypy proje wiki 'de [Python modülleri için saplamalar oluşturma](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) .
>
> mevcut olduğunda Visual Studio açıklamalarda tür ipuçlarını desteklemez.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Python 'un 3,5 öncesindeki sürümleri için Visual Studio, ayrıca, yazı türü olan *saplama dosyaları* (*. pyi*) aracılığıyla sağladığınız tür ipuçlarını da görüntüler. Doğrudan kodunuzda tür ipuçlarını dahil etmek istediğinizde veya doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğinizde, saplama dosyalarını kullanabilirsiniz. Daha fazla bilgi için bkz. mypy proje wiki 'de [Python modülleri için saplamalar oluşturma](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) .
>
> Visual Studio, Python 2 ve 3 için bir dizi yazı dosyası kümesi içerir, bu nedenle ek indirmeler gerekli değildir. Ancak, farklı bir dosya kümesi kullanmak istiyorsanız, **Araçlar**  >  **Seçenekler**  >  **Python**  >  **dil sunucusu** seçeneklerinde yolu belirtebilirsiniz. Bkz. [Seçenekler-dil sunucusu](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> mevcut olduğunda Visual Studio açıklamalarda tür ipuçlarını desteklemez.
::: moniker-end

### <a name="signature-help"></a>İmza yardımı

Bir işlevi çağıran kodu yazarken, açma 'yı yazdığınızda imza yardımı görünür `(` ve kullanılabilir belgeleri ve parametre bilgilerini görüntüler. Ayrıca,  +  + bir işlev çağrısının içinde CTRL vardiyası **alanıyla** görünmesini sağlayabilirsiniz. Görünen bilgiler, işlevin kaynak kodundaki belge dizelerine bağlıdır, ancak varsayılan değerleri içerir.

![Visual Studio düzenleyicisinde imza yardımı](media/code-editing-signature-help.png)

> [!Tip]
> İmza yardımını devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Python**  >  **genel** ' e gidin ve **ekstre tamamlama**  >  **parametresi bilgilerini** temizleyin.

### <a name="quick-info"></a>Hızlı bilgi

Bir tanımlayıcı üzerinde fare işaretçisinin üzerine gelindiğinde bir Hızlı Bilgi ipucu görüntülenir. Tanımlayıcıya bağlı olarak hızlı bilgi, olası değerler veya türler, kullanılabilir tüm belgeler, dönüş türleri ve tanım konumları gösterebilir:

![Visual Studio düzenleyicisinde hızlı bilgi](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kod renklendirme

Kod renklendirme kod analizinden renk değişkenlerine, deyimlerine ve kodunuzun diğer bölümlerine kadar bilgi kullanır. Örneğin, modüller veya sınıflara başvuran değişkenler, işlevlerden veya diğer değerlerden farklı bir renkte görünebilir ve parametre adları yerel veya genel değişkenlerden farklı bir renkle gösterilir. (Varsayılan olarak işlevler kalın olarak gösterilmez):

![Visual Studio düzenleyicisinde kod ve söz dizimi renklendirmesi](media/code-editing-code-coloring.png)

Renkleri özelleştirmek için, **Araçlar**  >  **Seçenekler**  >  **ortam**  >  **yazı tipleri ve renkler** ' e gidin ve **görüntüleme öğeleri** listesinde **Python** girdilerini değiştirin:

![Visual Studio yazı tipi ve renkler seçenekleri](media/code-editing-customize-colors.png)

> [!Tip]
> Kod renklendirmesini devre dışı bırakmak için, **Araçlar**  >  **Seçenekler**  >  **metin Düzenleyicisi**  >  **Python**  >  **Gelişmiş** ' e gidin ve türe göre **çeşitli seçenekler**  >  **renk adlarını** temizleyin. Bkz. [Seçenekler-çeşitli seçenekler](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

## <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, bir kısayol yazarak ve **Sekme** tuşuna basarak veya IntelliSense Kod Parçacığını Düzenle ve Komutlarla Çevrele komutlarını  >    >    **kullanarak, Python'ı** seçerek ve ardından istenen kod parçacığını seçerek dosyalarınıza eklenebiliyor kod parçalarıdır.

Örneğin, `class` bir sınıf tanımı ekser kod parçacığı için bir kısayoldur. kod parçacığını, yazarak otomatik tamamlama listesinde `class` görüntülebilirsiniz:

![Sınıf kısayolu için kod parçacığı](media/code-editing-code-snippet-class.png)

Tab **tuşuna** basılarak sınıfın geri kalanı oluşturulur. Ardından Sekme ile vurgulanan alanlar arasında hareket eden ad ve temeller  listesinin üzerine yazarak **Enter** tuşuna basarak gövdeyi yazmaya başlayabilirsiniz.

![Tamamlamanız için kod parçacığının alanlarını vurgular](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Menü komutları

IntelliSense **Kod Parçacığı Ekle** menü komutunu kullanarak Python'ı ve ardından bir kod  >    >   parçacığını seçersiniz: 

![Kod Parçacığı Ekle komutuyla kod parçacığı seçme](media/code-editing-code-snippet-insert.png)

Benzer **şekilde**  >  **IntelliSense** Surround'i Düzenle komutu, geçerli seçimi seçilen yapısal  >   öğenin içine metin düzenleyicisine yer verir. Örneğin, aşağıdakine benzer bir kodun olduğunu varsayalım:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Bu kodun ve Surround **With komutunun seçiminde** kullanılabilir kod parçacıklarının listesi görüntülenir. Listeden **def** seçildiğinde seçilen kod bir işlev tanımına eklenir  ve Sekme tuşuyla vurgulanan işlev adı ve bağımsız değişkenler arasında gezinebilirsiniz:

![Kod parçacıkları için Surround With komutunu kullanma](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Kullanılabilir kod parçacıklarını inceleme

Kullanılabilir kod parçacıklarını Kod Parçacıkları Yöneticisi'nde, Araçlar Kod Parçacıkları Yöneticisi menü komutu kullanılarak açılan ve dil olarak  >   **Python'ı** seçerek açabilirsiniz:

![Visual Studio'de Kod Parçacıkları Yöneticisi](media/code-editing-code-snippets-manager.png)

Kendi kod parçacıklarınızı oluşturmak için bkz. [Kılavuz: Kod parçacığı oluşturma.](../ide/walkthrough-creating-a-code-snippet.md)

Paylaşmak için harika bir kod parçacığı yazarsanız bunu bir gist'e yazıp bize [haber veabilirsiniz.](https://github.com/Microsoft/PTVS/issues) Bunu gelecekteki bir sürümde de dahil Visual Studio.

## <a name="navigate-your-code"></a>Kodunuzda gezinme

Visual Studio'da Python desteği, kaynak kodunun kullanılabilir olduğu kitaplıklar da dahil olmak üzere kodunuz içinde hızla gezinmek için çeşitli yol sağlar: gezinti [çubuğu,](#navigation-bar)Tanıma [**Git,**](#go-to-definition) [**Git**](#navigate-to)ve Tüm [**Başvuruları Bul.**](#find-all-references) Visual Studio [**Object Browser'Visual Studio kullanabilirsiniz.**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)

### <a name="navigation-bar"></a>Gezinti çubuğu

Gezinti çubuğu her düzenleyici penceresinin en üstünde görüntülenir ve iki düzeyli tanım listesi içerir. Sol açılan liste, geçerli dosyada üst düzey sınıf ve işlev tanımlarını içerir; sağ açılan listede, sol tarafta gösterilen kapsam içindeki tanımların listesi görüntülenir. Düzenleyicide ilerlerken listeler geçerli bağlamınızı gösterecek şekilde güncelleştirmesinin yanı sıra doğrudan atlamak için bu listelerden bir giriş de seçersiniz.

![Visual Studio düzenleyicisinde Gezinti Çubuğu](media/code-editing-navigation-bar.png)

> [!Tip]
> Gezinti çubuğunu gizlemek için Araçlar Seçenekler Metin **Düzenleyici**  >    >  Python **Genel'e gidin** ve Gezinti  >    >   **çubuğundan Ayarlar** için  >  **temizlemeniz gerekir.**

### <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git,** tanımlayıcının kullanımından (işlev adı, sınıf veya değişken gibi) tanımlandığı kaynak koda hızla atlar. Bir tanımlayıcıya sağ tıklar ve  Tanıma Git'i seçerek veya caret'i tanımlayıcıya yerleştirerek ve F12 tuşuna basarak **çağırabilirsiniz.** Kaynak kodun kullanılabilir olması şartıyla, kodunuz ve dış kitaplıklar genelinde çalışır. Kitaplık kaynak kodu kullanılamıyorsa **Tanıma** Git modül başvurusu için ilgili `import` deyime atlar veya bir hata görüntüler.

![Visual Studio'da Tanıma Git komutu](media/code-editing-go-to-definition.png)

### <a name="navigate-to"></a>Şu sayfaya gidin:

Git **Komutunu** Düzenle (  >   **Ctrl**, ), düzenleyicide herhangi bir dize yazarak kodunda bu dizeyi içeren bir işlev, sınıf veya değişken tanımlayan olası eşleşmeleri gördüğünüz bir arama kutusu + görüntüler. Bu özellik Tanıma Git ile benzer **bir özellik sağlar** ancak tanımlayıcının kullanımını bulmak zorunda kalmadan kullanılabilir.

Herhangi bir ada çift tıklayın veya ok tuşlarıyla ve **Enter** tuşlarıyla öğesini seçerek bu tanımlayıcının tanımına gidin.

![Visual Studio'da Git komutu](media/code-editing-navigate-to.png)

### <a name="find-all-references"></a>Tüm Başvuruları Bul

**Tüm Başvuruları Bul,** içeri aktarmalar ve atamalar dahil olmak üzere belirli bir tanımlayıcının tanımlandığı ve kullanılan yeri bulmanın yararlı bir yolu olur. Bir tanımlayıcıya sağ tıklar ve Tüm Başvuruları Bul'ı seçerek veya caret'i tanımlayıcıya yerleştirerek ve **Shift** F12 tuşuna basarak + **çağırabilirsiniz.** Listede bir öğeye çift tıklar ve bu öğenin bulunduğu konuma giditir.

![Tüm Başvuruları Bul sonuçları](media/code-editing-find-all-references.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Biçimlendirme](formatting-python-code.md)
- [Yeniden Düzenle](refactoring-python-code.md)
- [Linter kullanma](linting-python-code.md)
