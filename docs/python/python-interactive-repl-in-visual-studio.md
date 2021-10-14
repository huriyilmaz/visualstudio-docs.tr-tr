---
title: Python etkileşimli penceresi (REPL)
description: Hızlı Python kodu geliştirme için etkileşimli pencereyi (REPL) Visual Studio.
ms.date: 02/11/2019
ms.topic: how-to
author: rjmolyneaux
ms.author: rmolyneaux
manager: jmartens
ms.technology: vs-python
ms.workload:
- python
- data-science
ms.openlocfilehash: 3000cf5f02e4519f6218bdd9be7633434482a029
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129972992"
---
# <a name="work-with-the-python-interactive-window"></a>Python Etkileşimli penceresi

Visual Studio Python ortamlarınızı her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar.  Bu pencere, komutpython.exerePL ile elde edersiniz. Etkileşimli **pencere** (Diğer Öğeleri Görüntüle **ve**  >  **Etkileşimli Windows** komutlarıyla açılır), rastgele Python kodu girmenize ve anında sonuçları  >  görmenize olanak **&lt; &gt;** sağlar. Bu kodlama yolu, API'leri ve kitaplıkları öğrenmenize, denemenize ve projelerinize dahil etmek için etkileşimli olarak çalışma kodu geliştirmenize yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio birkaç Python REPL modu vardır:

| ÇOĞALTMA | Description | Düzenleme | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, Python ile doğrudan konuşma | Standart düzenleme (çok satırlı vb.). | Evet, aracılığıyla `$attach` | No |
| Hata Ayıklama | Varsayılan REPL, hata ayıklamalı Python işlemiyle konuşma | Standart düzenleme | Yalnızca hata ayıklama | No |
| IPython | REPL, IPython arka ucuyla sohbet ediyor | IPython komutları, Pylab kolaylıkları | No | Evet, REPL'de satır içi |
| Pylab ile IPython | REPL, IPython arka ucuyla sohbet ediyor | Standart IPython | No | Evet, ayrı pencere |

Bu makalede Standart ve **HATA AYıKLAMA** **REPL** modları açıklanmıştır. IPython modları hakkında ayrıntılı bilgi için [bkz. IPython REPL'yi kullanma.](interactive-repl-ipython.md)

Ctrl Enter gibi düzenleyiciyle etkileşimler de dahil olmak üzere örneklerle ilgili ayrıntılı bir kılavuz için + bkz. [Öğretici 3. Adım: Etkileşimli REPL penceresini kullanma.](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="open-an-interactive-window"></a>Bir Etkileşimli penceresi

Bir ortam için Etkileşimli pencereyi **açmanın** birkaç yolu vardır.

İlk olarak Python Ortamları penceresine **(** Python  >  **Ortamlarını Görüntüle Windows**  >  **Veya** **Ctrl** + **K**  >  **Ctrl**) + **`**  ve seçilen ortam için Etkileşimli Pencere Aç komutunu veya düğmesini seçin.

![Python Ortamları penceresindeki Etkileşimli Pencere bağlantısı](media/interactive-window-opening.png)

İkincisi, Diğer Öğeleri Görüntüle  >  **menüsünün Windows** yakın bir yerde varsayılan ortamınız için **bir Python** Etkileşimli Pencere komutu  ve Ortamlar penceresine geçiş komutu vardır:

![Görünüm'de Etkileşimli Pencere menü öğeleri > Diğer Windows](media/interactive-window-menu.png)

Üçüncüsü, Projenizin  başlangıç dosyasında veya tek başına bir dosya   >  **\<Project | File> için, Python Etkileşimli'de** Yürüt'te Hata Ayıkla menü komutunu (**Shift** + **Alt** F5) seçerek etkileşimli bir pencere + **açabilirsiniz:**

![Python Project menüsünde yürütme](media/interactive-execute-project.png)

Son olarak, dosyada kod seçerek aşağıda açıklanan [ **Etkileşimliye Gönder komutunu**](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli penceresi seçenekleri

Araçlar Seçenekler  Python Interactive Windows (bkz. Seçenekler) aracılığıyla Etkileşimli pencerenin  >    >    >  **çeşitli** yönlerini kontrol [edin:](python-support-options-and-settings-in-visual-studio.md)

![Python etkileşimli pencere seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli penceresi

Etkileşimli **pencere** açıldıktan sonra, isteminde satır satır kod girmeye **\>\>\>** başlayabilirsiniz. Etkileşimli **pencere,** her satırı siz girerken yürütür. Bu satır modül içeri aktarmayı, değişkenleri tanımlamayı ve daha birçok işlemi içerir:

![Python etkileşimli penceresi](media/interactive-window.png)

Bunun istisnası, tam bir deyim yapmak için yukarıda gösterildiği gibi bir deyimin iki nokta üst üste ile sona erdiğinde olduğu gibi `for` ek kod satırlarının gerekli olduğu durumdur. Bu durumlarda, yukarıdaki grafikte dördüncü ve beşinci satırlarda gösterildiği gibi satır istemi **...** olarak değişir ve bu da blok için ek satırlar girmeniz gerektiğini ifade ediyor. Boş bir **satırda Enter** tuşuna **basıyorsanız Etkileşimli** pencere bloğu kapatır ve yorumlayıcıda çalıştırır.

> [!Tip]
> Etkileşimli **pencere,** çevresindeki bir kapsama ait olan deyimleri otomatik olarak girintileerek normal Python komut satırı REPL deneyimini iyiler. Geçmişi (yukarı okla geri çağrılır) çok satırlı öğeler de sağlarken, komut satırı REPL yalnızca tek satır sağlar.

<a name="meta-commands"></a> Etkileşimli **pencere** çeşitli meta komutları da destekler. Tüm meta komutlar ile başlar ve yazarak meta komutların listesini ve belirli bir komutun kullanım `$` `$help` ayrıntılarını `$help <command>` edinebilirsiniz.

:::moniker range="<=vs-2017"

| Meta komutu | Description |
| --- | --- |
| `$$` | Oturum boyunca kod açıklaması yapmak için yararlı olan bir açıklama ekler. |
| `$attach` | Hata ayıklamayı etkinleştirmek Visual Studio hata ayıklayıcısını REPL pencere sürecine iliştirer. |
| `$cls`, `$clear` | Geçmiş ve yürütme bağlamını olduğu gibi bırakarak düzenleyici penceresinin içeriğini temizler. |
| `$help` | Komutların listesini veya belirli bir komutla ilgili yardımı görüntüleme. |
| `$load` | Dosyadan komutları yükler ve tamamlayana kadar yürütülür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına geçiştir. |
| `$reset` | Yürütme ortamını başlangıç durumuna sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

:::moniker-end

:::moniker range=">=vs-2019"

| Meta komutu | Description |
| --- | --- |
| `$$` | Oturum boyunca kod açıklaması yapmak için yararlı olan bir açıklama ekler. |
| `$cls`, `$clear` | Geçmiş ve yürütme bağlamını olduğu gibi bırakarak düzenleyici penceresinin içeriğini temizler. |
| `$help` | Komutların listesini veya belirli bir komutla ilgili yardımı görüntüleme. |
| `$load` | Dosyadan komutları yükler ve tamamlayana kadar yürütülür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına geçiştir. |
| `$reset` | Yürütme ortamını başlangıç durumuna sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

:::moniker-end

Komutlar, uygulama ve dışarı Visual Studio tarafından da genişletilebilir `IInteractiveWindowCommand` ([örneğin).](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)

## <a name="switch-scopes"></a>Kapsamları değiştirme

Varsayılan olarak, **bir** projenin Etkileşimli penceresinin kapsamı, komut isteminden çalıştırmış gibi projenin başlangıç dosyası olarak gösterilir. Tek başına bir dosya için bu dosyanın kapsamını belirtir. Ancak REPL oturumunuz sırasında herhangi bir zamanda Etkileşimli pencerenin üst kısmında yer alan açılan menü **kapsamı** değiştirmenizi sağlar:

![Etkileşimli penceresi kapsamları](media/interactive-scopes.png)

Bir modülü (yazma gibi) içeri aktardıktan sonra, bu modülde herhangi bir kapsama `import importlib` geçmek için açılan açılır liste seçenekleri görüntülenir. Etkileşimli pencereye **gelen** bir ileti yeni kapsamı da gösterir, böylece oturumunuz sırasında belirli bir durumuna nasıl varmanızı izleyebilirsiniz.

Bir `dir()` kapsama girerek işlev adları, sınıflar ve değişkenler de dahil olmak üzere bu kapsamda geçerli tanımlayıcılar görüntülenir. Örneğin, ve `import importlib` ardından kullanılarak `dir()` aşağıdakiler gösterir:

![Etkileşimli penceresi kapsamına alma](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli'ye gönder komutu

Doğrudan Etkileşimli pencere içinde çalışmaya **ek** olarak düzenleyicide kod seçebilir, sağ  tıklar ve Etkileşimliye Gönder'i seçebilir veya Ctrl Enter **tuşuna** + **basabilirsiniz.**

![Etkileşimli menüye gönder komutu](media/interactive-send-to.png)

Bu komut, kodunuzu geliştirirken test etmek de dahil olmak üzere, iterative veya evrimsel kod geliştirme için yararlıdır. Örneğin Etkileşimli pencereye bir kod parçası göndererek çıkışını gördükte yukarı oka basarak kodu yeniden gösterebilir, değiştirebilir ve **Ctrl** Enter tuşlarına basarak hızlı bir şekilde  + **testebilirsiniz.** **(Girişin** sonunda Enter tuşuna basılarak yürütülür, ancak girişin **ortasındaki Enter** tuşuna basılarak bir yeni satır ekler.) Koda sahip olduktan sonra kolayca proje dosyanıza kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual Studio ve **>>>** **...** REPL, Etkileşimli penceresinden düzenleyiciye **kod yapıştırıyorken** istemler. Yapıştır rePL istemlerini kaldırır **seçeneğini** kullanarak Araçlar Seçenekler Metin Düzenleyici  >    >    >  **Python**  >   Gelişmiş sekmesinde bu **davranışı değiştirebilirsiniz.** Bkz. [Seçenekler - Çeşitli seçenekler.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleri ile çalışma

Kod hücreleri veri analizinde kullanılabilir ve çeşitli metin düzenleyicileri tarafından de destekler.

Örneğin, bir kod dosyasını karalama paneli olarak kullanırken, genellikle tümünü tek seferde göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplamak için, hücrenin başlangıcına başlayarak bir açıklama ekleyerek kodu bir *kod hücresi* olarak işaretleyin `#%%` , bu da öncekini sonlandırır. Kod hücreleri daraltılabilse ve genişletilebilir ve  + bir kod hücresinin içinde CTRL **ENTER** kullanılması, tüm hücreyi **etkileşimli** pencereye gönderir ve bir sonrakine gider.

Visual Studio ayrıca `# In[1]:` , bir jupyter not defterini Python dosyası olarak dışa aktarırken aldığınız biçim olan gibi açıklamalarla başlayan kod hücrelerini de algılar. bu algılama, Python dosyası olarak indirerek [Azure Notebooks](https://notebooks.azure.com/) bir not defterini çalıştırmayı, Visual Studio açmayı ve her hücreyi çalıştırmak için **Ctrl** + **Enter** tuşunu kullanmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

**Etkileşimli** pencere, IntelliSense 'in yalnızca kaynak kodu analizini temel alan kod düzenleyiciden farklı olarak, canlı nesneleri temel alan IntelliSense 'i içerir. Bu öneriler, özellikle dinamik olarak üretilen kodla **etkileşimli** pencerede daha doğrudur. Dezavantajı, yan etkileri olan işlevlerin (örneğin, günlük mesajları) geliştirme deneyiminizi etkileyebileceğini unutmayın.

bu davranış bir sorun ise,   >    >    >  [seçenekler etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)bölümünde açıklandığı gibi, **tamamlama modu** grubundaki araçlar seçenekler Python **etkileşimli Windows** altındaki ayarları değiştirin.
