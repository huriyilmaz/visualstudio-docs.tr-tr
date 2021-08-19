---
title: Python kodunu düzenleme
description: Python için Visual Studio, biçimlendirme, linting ve yeniden düzenlemenin yanı sıra zengin IntelliSense, kod parçacıkları ve gezinti özellikleri sağlar.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076353"
---
# <a name="edit-python-code"></a>Python kodunu düzenleme

Geliştirme sürenizin büyük bir çoğunu kod düzenleyicisinde harcadığınız için, [Visual Studio Python](installing-python-support-in-visual-studio.md) desteği daha üretken çalışmanıza yardımcı olacak işlevler sağlar. IntelliSense söz dizimi vurgulama, otomatik tamamlama, imza yardımı, yöntem geçersiz kılmaları, arama ve gezinti özellikleridir.

Düzenleyici ayrıca etkileşimli pencereyle **tümleşiktir** Visual Studio ikisi arasında kod değişimini kolaylaştırır. Ayrıntılar [için bkz. Öğretici 3. Adım:](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md) Etkileşimli REPL penceresini kullanma ve Etkileşimli penceresi - [Etkileşimli'ye Gönder](python-interactive-repl-in-visual-studio.md#send-to-interactive-command) komutunu kullanma.

Kod düzenleyicisinde kodu düzenleme hakkında Visual Studio için [bkz. Kod düzenleyicisinin özellikleri.](../ide/writing-code-in-the-code-and-text-editor.md) Ayrıca [kodunuzun belirli bölümlerine](../ide/outlining.md)odaklanmanıza yardımcı olan Outlining (Açıklama) bölümlerine de bakın.

Ayrıca, her modülde tanımlanan Python sınıflarını ve bu sınıflarda tanımlanan işlevleri incelemek için Visual Studio **Object Browser** **(** View  >  **Other Windows**  >  **Object Browser** veya **Ctrl** + **W**  >  **J**) kullanabilirsiniz.

## <a name="intellisense"></a>IntelliSense

IntelliSense [tamamlamalar,](#completions)imza [yardımı,](#signature-help) [hızlı bilgi](#quick-info)ve [kod renklendirmesi sağlar.](#code-coloring) Visual Studio 2017 sürüm 15.7 ve sonraki sürümler de tür [ipuçlarını destekler.](#type-hints)

Performansı artırmak için Visual Studio 2017 sürüm 15.5 ve önceki sürümlerde IntelliSense, projenizin her Python ortamı için oluşturulan tamamlama veritabanına bağlıdır. Paketleri eklemeniz, kaldırmanız veya güncelleştirmeniz gerekirse veritabanlarının yenilenmesi gerekir. Veritabanı durumu, **IntelliSense** **sekmesindeki Python** Ortamları penceresinde **(Çözüm Gezgini)** gösterilir (bkz. [Ortamlar penceresi başvurusu).](python-environments-window-tab-reference.md)

Visual Studio 2017 sürüm 15.6 ve sonraki sürümler, veritabanına bağımlı olmayan IntelliSense tamamlamaları sağlamak için farklı bir şekilde kullanılır.

### <a name="completions"></a>Tamamlamalar

Tamamlamalar, düzenleyicide geçerli konuma uygun şekilde girilebilir deyimler, tanımlayıcılar ve diğer sözcükler olarak görünür. Listede gösterilenler bağlama dayalıdır ve yanlış veya dikkat dağıtan seçenekleri atacak şekilde filtrelenmiş. Tamamlamalar genellikle farklı deyimler (örneğin) ve işleçler (nokta dahil) yazarak tetiklenir, ancak Ctrl J Ara Çubuğu yazarak istediğiniz zaman görünmesini `import`  +   >  **sebilirsiniz.**

![Visual Studio düzenleyicisinde üye tamamlama](media/code-editing-completions-simple.png)

Bir tamamlama listesi açık olduğunda, ok tuşlarını, fareyi kullanarak veya türe devam etmek için istediğiniz tamamlamayı arayabilirsiniz. Daha fazla harf yazarak büyük olasılıkla tamamlanmaları gösterecek şekilde liste daha fazla filtrelenmiş olur. Aşağıdakiler gibi kısayolları da kullanabilirsiniz:

- Adın başında yer alan harfler ('argparse' bulmak için 'parse' gibi) yazma
- 'AbstractBaseClass' veya 'air' sözcüklerini bulmak için yalnızca sözcüklerin başındaki harfleri ('abc' gibi) as_integer_ratio
- 'base64' bulmak için "b64" gibi harfleri atlama

Bazı örnekler:

![Düzenleyicide filtreleme ile üye Visual Studio tamamlama](media/code-editing-completion-filtering.png)

Üye tamamlamaları, olası türlerin yöntemleri ve öznitelikleriyle birlikte bir değişken veya değerden sonra nokta yazarak otomatik olarak görüntülenir. Bir değişken birden fazla türde olabilirse, liste tüm türlerden tüm olasılıkları içerir ve her tamamlamayı destekleyen türleri gösteren ek bilgiler içerir. Bir tamamlamanın tüm olası türler tarafından desteklenesi, ek açıklama olmadan gösterilir.

![Düzenleyicide birden çok türde üye Visual Studio tamamlama](media/code-editing-completion-types.png)

Varsayılan olarak, "dunder" üyeleri (çift alt çizgiyle başlayan ve biten üyeler) gösterilmez. Genel olarak, bu tür üyelere doğrudan erişilmamalı. Ancak, bir alt çizgiye ihtiyacınız varsa, başındaki çift alt çizgi yazarak bu tamamlamalar listeye eklenir:

![Visual Studio düzenleyicisinde özel üye tamamlama](media/code-editing-completion-dunder.png)

ve `import` `from ... import` deyimleri, içe aktarılmış modüllerin listesini görüntüler. ile `from ... import` liste, belirtilen modülden içe aktarabilirsiniz üyeleri içerir.

![Visual Studio düzenleyicisinde içeri aktarma tamamlama](media/code-editing-completion-import.png)

ve `raise` `except` deyimleri, büyük olasılıkla hata türleri olan sınıfların listelerini görüntüler. Liste tüm kullanıcı tanımlı özel durumları içermeyebilirsiniz, ancak uygun yerleşik özel durumları hızla bulumanıza yardımcı olur:

![Visual Studio düzenleyicisinde özel durum tamamlama](media/code-editing-completion-exception.png)

@ yazarak bir dekoratör başlatılır ve olası dekoratörler gösterir. Bu öğelerin çoğu dekoratör olarak kullanılamaz; Hangisinin kullanılamayacaklarını belirlemek için kitaplık belgelerini inceleyin.

![Visual Studio düzenleyicisinde dekoratör tamamlama](media/code-editing-completion-decorator.png)

> [!Tip]
> Araç Seçenekleri Metin Düzenleyici Python Gelişmiş aracılığıyla  >    >  **tamamlamaların davranışını**  >    >  **yapılandırabilirsiniz.** Bunların **arasında,** Siz yazarak tamamlama önerileri filtrelemeyi arama dizesine göre  filtrele (varsayılan olarak işaretlidir) ve Üye tamamlaması üyelerin kesişimlerini yalnızca tüm olası türler tarafından desteklenen tamamlamaları gösterir (varsayılan seçenek işaretlenmemiştir). Bkz. [Seçenekler - tamamlama sonuçları.](python-support-options-and-settings-in-visual-studio.md#completion-results)

### <a name="type-hints"></a>Tür ipuçları

*Visual Studio 2017 sürüm 15.7 ve sonrası.*

Python 3.5+ 'da "Tür ipuçları" ([PEP 484](https://www.python.org/dev/peps/pep-0484/) (python.org), bağımsız değişken, dönüş değeri ve sınıf öznitelikleri türlerini belirten işlevler ve sınıflar için ek açıklama söz dizimidir. IntelliSense, bu ek açıklamalara sahip işlev çağrılarını, bağımsız değişkenleri ve değişkenlerin üzerine gelindiğinde tür ipuçlarını görüntüler.

Aşağıdaki örnekte sınıfı olarak bildirildi ve işlevi hem bağımsız değişkenleri hem de dönüş `Vector` değeri için tür ipuçları `List[float]` `scale` içerir. Bu işlev çağrısının üzerine gelindiğinde tür ipuçları yer almaktadır:

![Tür ipuçlarını ortaya çıkarmak için işlev çağrısının üzerine gelme](media/code-editing-type-hints1.png)

Aşağıdaki örnekte, sınıfın açıklamalı özniteliklerinin bir öznitelik için IntelliSense tamamlama açılan menüsünde nasıl `Employee` görüntülenmiş olduğunu görürsünüz:

![Tür ipuçlarını gösteren IntelliSense tamamlaması](media/code-editing-type-hints2.png)

Hatalar normalde çalışma süresine kadar görünmeyeceği için projeniz genelinde tür ipuçlarını doğrulamak da yararlıdır. Bu amaçla Visual Studio, python Run Mypy in Çözüm Gezgini bağlam menüsü komutu aracılığıyla endüstri standardı  >  **MyPy** **aracını tüm Çözüm Gezgini:**

![MyPy bağlam menüsü komutunu Çözüm Gezgini](media/code-editing-type-hints-run-mypy.png)

komutunu çalıştırarak gerekirse mypy paketini yüklemeniz istenir. Visual Studio projede her Python dosyasında tür ipuçlarını doğrulamak için mypy çalıştırır. Hata Listesi penceresinde Visual Studio **görüntülenir.** Pencerede bir öğenin seçerek kodunda uygun satıra gidin.

Basit bir örnek olarak, aşağıdaki işlev tanımı bağımsız değişkenin türünde olduğunu belirten bir tür ipucu içerirken, bu işleve yapılan çağrı bir `input` `str` tamsayıyı geçmeyi dener:

```python
def commas_to_colons(input: str):
    items = input.split(',')
    items = [x.strip() for x in items]
    return ':'.join(items)

commas_to_colons(1)
```

Bu **kodda Mypy'yi** Çalıştır komutunun kullanımı aşağıdaki hatayı üretir:

![Mypy doğrulama türü ipuçlarının örnek sonucu](media/code-editing-type-hints-validation-error.png)

::: moniker range="vs-2017"
> [!Tip]
> Python'ın 3.5'Visual Studio sürümleri için, *Typeshed* saplama dosyaları (*.pyi)* aracılığıyla temin edersiniz tür ipuçlarını da görüntüler. Saplama dosyalarını doğrudan kodunuza tür ipuçları eklemek istemeden veya bunları doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğiniz her zaman kullanabilirsiniz. Daha fazla bilgi için mypy [projesi wiki'sinde Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) modülleri için saplamalar oluşturma makalesini bakın.
>
> Şu anda Visual Studio tür ipuçlarını desteklemez.
::: moniker-end
::: moniker range=">=vs-2019"
> [!Tip]
> Python'ın 3.5'Visual Studio sürümleri için, *Typeshed* saplama dosyaları (*.pyi)* aracılığıyla temin edersiniz tür ipuçlarını da görüntüler. Saplama dosyalarını doğrudan kodunuza tür ipuçları eklemek istemeden veya bunları doğrudan kullanmayan bir kitaplık için tür ipuçları oluşturmak istediğiniz her zaman kullanabilirsiniz. Daha fazla bilgi için mypy [projesi wiki'sinde Python](https://github.com/python/mypy/wiki/Creating-Stubs-For-Python-Modules) modülleri için saplamalar oluşturma makalesini bakın.
>
> Visual Studio Python 2 ve 3 için Typeshed dosyaları paket kümesi içerir, bu nedenle ek indirmeler gerekmez. Ancak, farklı bir dosya kümesi kullanmak için, Yolu Araçlar Seçenekleri Python Dil Sunucusu  >    >    >  **seçeneklerinde belirtebilirsiniz.** Bkz. [Seçenekler - Dil Sunucusu](python-support-options-and-settings-in-visual-studio.md#language-server-options).
>
> Şu anda Visual Studio tür ipuçlarını desteklemez.
::: moniker-end

### <a name="signature-help"></a>İmza yardımı

bir işlevi çağıran kod yazarken, açılış yazınca imza yardımı görünür ve kullanılabilir `(` belgeleri ve parametre bilgilerini görüntüler. Bir işlev çağrısının içinde **Ctrl** + **Shift** + **Tuşu ile görünmesini** de sabilirsiniz. Görüntülenen bilgiler, işlevin kaynak kodundaki belge dizelerini kullanır ancak varsayılan değerleri içerir.

![Visual Studio düzenleyicisinde imza yardımı](media/code-editing-signature-help.png)

> [!Tip]
> İmza yardım kutusunu devre dışı bırakmak için Araçlar **Seçenekler Metin** Düzenleyicisi Python  >    >  **Genel'e** gidin ve Deyim  >    >   tamamlama **Parametre**  >  **bilgilerini temizlenin.**

### <a name="quick-info"></a>Hızlı bilgiler

Fare işaretçisinin bir tanımlayıcının üzerine gelindiğinde bir Hızlı Bilgi ipucu. Tanımlayıcıya bağlı olarak, Hızlı Bilgi olası değerleri veya türleri, kullanılabilir tüm belgeleri, dönüş türlerini ve tanım konumlarını görüntüler:

![Visual Studio Düzenleyicisi'nde Hızlı Bilgi](media/code-editing-quick-info.png)

### <a name="code-coloring"></a>Kod renklendirme

Kod renklendirme, kod analizinden değişkenleri, deyimleri ve kodunuzun diğer bölümlerini renklendirmeye kadar olan bilgileri kullanır. Örneğin, modüllere veya sınıflara başvuran değişkenler işlevlerden veya diğer değerlerden farklı bir renkle gösterebilirsiniz ve parametre adları yerel veya genel değişkenlerden farklı bir renkte görünür. (Varsayılan olarak işlevler kalın olarak gösterilmez):

![Düzenleyicide kod ve söz Visual Studio renklendirme](media/code-editing-code-coloring.png)

Renkleri özelleştirmek için Araçlar Seçenekler Ortam Yazı  >  **Tipleri**  >  **ve**  >  **Renkler'e gidin** ve Öğeleri görüntüle listesinde **Python** **girişlerini** değiştirebilirsiniz:

![Visual Studio'daki Yazı Tipleri ve Renkler seçenekleri](media/code-editing-customize-colors.png)

> [!Tip]
> Kod renklendirmeyi devre dışı bırakmak için **Araçlar Seçenekler** Metin Düzenleyici Python Gelişmiş'e gidin ve türüne göre Çeşitli  >    >    >    >   **Seçenekler**  >  **Renk adları'nın temizlerini açın.** Bkz. [Seçenekler - Çeşitli seçenekler.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

## <a name="code-snippets"></a>Kod parçacıkları

Kod parçacıkları, bir kısayol yazarak ve **Sekme** tuşuna basarak veya IntelliSense Kod Parçacığını Düzenle ve Komutlarla Çevrele komutlarını  >    >    **kullanarak, Python'ı** seçerek ve ardından istenen kod parçacığını seçerek dosyalarınıza eklenebiliyor kod parçalarıdır.

Örneğin, `class` bir sınıf tanımı ekser kod parçacığı için bir kısayoldur. kod parçacığını, yazarak otomatik tamamlama listesinde `class` görüntülebilirsiniz:

![Sınıf kısayolu için kod parçacığı](media/code-editing-code-snippet-class.png)

Tab **tuşuna** basılarak sınıfın geri kalanı oluşturulur. Ardından Sekme ile vurgulanan alanlar arasında hareket eden ad ve temeller  listesinin üzerine yazarak **Enter** tuşuna basarak gövdeyi yazmaya başlayabilirsiniz.

![Tamamlamanız için kod parçacığının alanlarını vurgular](media/code-editing-code-snippets.png)

### <a name="menu-commands"></a>Menü komutları

IntelliSense **Kod Parçacığı** Ekle menü komutunu kullanarak Python'ı ve ardından bir kod  >    >   parçacığını seçersiniz:

![Kod Parçacığı Ekle komutuyla kod parçacığı seçme](media/code-editing-code-snippet-insert.png)

Benzer **şekilde**  >  **IntelliSense** Surround'i Düzenle komutu, geçerli seçimi seçilen yapısal  >   öğenin içine metin düzenleyicisine yer verir. Örneğin, aşağıdakine benzer bir kodun olduğunu varsayalım:

```python
sum = 0
for x in range(1, 100):
    sum = sum + x
```

Bu kodun ve Surround **With komutunun seçiminde** kullanılabilir kod parçacıklarının listesi görüntülenir. Listeden **def** seçildiğinde seçilen kod bir işlev tanımına eklenir ve **Sekme** tuşuyla vurgulanan işlev adı ile bağımsız değişkenler arasında gezinebilirsiniz:

![Kod parçacıkları için Surround With komutunu kullanma](media/code-editing-code-snippet-surround-with.png)

### <a name="examine-available-snippets"></a>Kullanılabilir kod parçacıklarını inceleme

Kullanılabilir kod parçacıklarını Kod Parçacıkları Yöneticisi'nde, Araçlar Kod Parçacıkları Yöneticisi menü komutu kullanılarak açılan ve dil olarak  >   **Python'ı** seçerek açabilirsiniz:

![Visual Studio'de Kod Parçacıkları Yöneticisi](media/code-editing-code-snippets-manager.png)

Kendi kod parçacıklarınızı oluşturmak için bkz. [Adım adım kılavuz: Kod parçacığı oluşturma.](../ide/walkthrough-creating-a-code-snippet.md)

Paylaşmak için harika bir kod parçacığı yazarsanız bunu bir gist'e yazıp bize [haber veabilirsiniz.](https://github.com/Microsoft/PTVS/issues) Bunu gelecekteki bir sürümde de dahil Visual Studio.

## <a name="navigate-your-code"></a>Kodunuzda gezinme

Visual Studio'de Python desteği, kaynak kodunun kullanılabilir olduğu kitaplıklar da dahil olmak üzere kodunuz içinde hızla gezinmek için çeşitli yol sağlar: gezinti [çubuğu,](#navigation-bar)Tanıma [**Git,**](#go-to-definition) [**Git**](#navigate-to), Git ve Tüm [**Başvuruları Bul.**](#find-all-references) Visual Studio [**Object Browser'Visual Studio da kullanabilirsiniz.**](../ide/viewing-the-structure-of-code.md#BKMK_ObjectBrowser)

### <a name="navigation-bar"></a>Gezinti çubuğu

Gezinti çubuğu her düzenleyici penceresinin en üstünde görüntülenir ve iki düzeyli tanım listesi içerir. Sol açılan liste, geçerli dosyada üst düzey sınıf ve işlev tanımlarını içerir; sağ açılan listede, sol tarafta gösterilen kapsam içindeki tanımların listesi görüntülenir. Düzenleyicide ilerlerken listeler geçerli bağlamınızı gösterecek şekilde güncelleştirmesinin yanı sıra doğrudan atlamak için bu listelerden bir giriş de seçersiniz.

![Visual Studio düzenleyicisinde Gezinti Çubuğu](media/code-editing-navigation-bar.png)

> [!Tip]
> Gezinti çubuğunu gizlemek için Araçlar Seçenekler Metin **Düzenleyicisi**  >    >  Python **Genel'e gidin** ve Gezinti  >    >   **çubuğundan Ayarlar** için  >  **temizlemeniz gerekir.**

### <a name="go-to-definition"></a>Tanıma Git

**Tanıma Git,** tanımlayıcının kullanımından (işlev adı, sınıf veya değişken gibi) tanımlandığı kaynak koda hızla atlar. Bir tanımlayıcıya sağ tıklar ve  Tanıma Git'i seçerek veya caret'i tanımlayıcıya yerleştirerek ve F12 tuşuna basarak **çağırabilirsiniz.** Kaynak kodun kullanılabilir olması şartıyla, kodunuz ve dış kitaplıklar genelinde çalışır. Kitaplık kaynak kodu kullanılamıyorsa **Tanıma** Git modül başvurusu için ilgili `import` deyime atlar veya bir hata görüntüler.

![Visual Studio'de Tanıma Git komutu](media/code-editing-go-to-definition.png)

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
