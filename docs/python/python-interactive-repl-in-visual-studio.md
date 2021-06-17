---
title: Python etkileşimli penceresi (REPL)
description: Hızlı Python kodu geliştirme için etkileşimli pencereyi (REPL) Visual Studio.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 21115673a41e26b2f1685442d2ed0ad93a147990
ms.sourcegitcommit: 4908561809ad397c99cf204f52d5e779512e502c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112254894"
---
# <a name="work-with-the-python-interactive-window"></a>Python Etkileşimli penceresi

Visual Studio Python ortamlarınızı her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar.  Bu pencere, komutpython.exerepl ile elde edersiniz. Etkileşimli **pencere** (Diğer Windows ortamını **Görüntüle** Etkileşimli menü komutlarıyla açılır), rastgele Python kodu girmenize ve anında  >    >  sonuçları görmenize olanak **&lt; &gt;** sağlar. Bu kodlama yolu, API'leri ve kitaplıkları öğrenmenize, denemenize ve projelerinize dahil etmek için etkileşimli olarak çalışma kodu geliştirmenize yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio bir dizi Python REPL modu vardır:

| Çoğaltma | Açıklama | Düzenleme | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, Python ile doğrudan konuşma | Standart düzenleme (çok satırlı vb.). | Evet, aracılığıyla `$attach` | Hayır |
| Hata Ayıklama | Varsayılan REPL, hata ayıklamalı Python işlemiyle konuşma | Standart düzenleme | Yalnızca hata ayıklama | Hayır |
| IPython | REPL, IPython arka ucuyla sohbet ediyor | IPython komutları, Pylab kolaylıkları | Hayır | Evet, REPL'de satır içi |
| Pylab ile IPython | REPL, IPython arka ucuyla sohbet ediyor | Standart IPython | Hayır | Evet, ayrı pencere |

Bu makalede Standart ve **HATA AYıKLAMA** **REPL** modları açıklanmıştır. IPython modları hakkında ayrıntılı bilgi için [bkz. IPython REPL'yi kullanma.](interactive-repl-ipython.md)

**Ctrl** Enter gibi düzenleyiciyle etkileşimler de dahil olmak üzere örneklerle ilgili ayrıntılı bir kılavuz için + bkz. [Öğretici 3. Adım: Etkileşimli REPL penceresini kullanma.](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="open-an-interactive-window"></a>Bir Etkileşimli penceresi

Bir ortam için Etkileşimli pencereyi **açmanın** birkaç yolu vardır.

İlk olarak Python Ortamları penceresine **(** Diğer Windows Python Ortamlarını Görüntüle veya  >    >   **Ctrl** + **K**  >  **Ctrl**) + **`**  ve seçili ortam için Etkileşimli Pencere Aç komutunu veya düğmesini seçin.

![Python Ortamları penceresindeki Etkileşimli Pencere bağlantısı](media/interactive-window-opening.png)

İkincisi, Diğer   >  **Windows'u** Görüntüle menüsünün alt kısmında, varsayılan ortamınız için bir **Python** Etkileşimli Pencere  komutu ve Ortamlar penceresine geçiş komutu vardır:

![Diğer Windows'ları Görüntüle'> Etkileşimli Pencere menü öğeleri](media/interactive-window-menu.png)

Üçüncüsü, Projenizin  başlangıç dosyasında veya tek başına bir dosya   >  **\<Project | File> için, Python Etkileşimli'de** Yürüt'te Hata Ayıkla menü komutunu (**Shift** + **Alt** F5) seçerek etkileşimli bir pencere + **açabilirsiniz:**

![Python Etkileşimli menüsünde Projeyi Yürütme](media/interactive-execute-project.png)

Son olarak, dosyada kod seçerek aşağıda açıklanan [ **Etkileşimliye Gönder komutunu**](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli penceresi seçenekleri

Araçlar Seçenekler Python Etkileşimli Windows aracılığıyla **Etkileşimli** pencerenin çeşitli **yönlerini**  >    >    >  **kontrol edin** (bkz. [Seçenekler):](python-support-options-and-settings-in-visual-studio.md)

![Python etkileşimli pencere seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli penceresi

Etkileşimli **pencere** açıldıktan sonra, isteminde satır satır kod girmeye **\>\>\>** başlayabilirsiniz. Etkileşimli **pencere,** her satırı siz girerken yürütür. Bu satır modül içeri aktarmayı, değişkenleri tanımlamayı ve daha birçok işlemi içerir:

![Python etkileşimli penceresi](media/interactive-window.png)

Bunun istisnası, tam bir deyim yapmak için yukarıda gösterildiği gibi bir deyimin iki nokta üst üste ile sona erdiğinde olduğu gibi `for` ek kod satırlarının gerekli olduğu durumdur. Bu durumlarda, yukarıdaki grafikte dördüncü ve beşinci satırlarda gösterildiği gibi satır istemi **...** olarak değişir ve bu da blok için ek satırlar girmeniz gerektiğini ifade ediyor. Boş bir **satırda Enter** tuşuna **basıyorsanız Etkileşimli** pencere bloğu kapatır ve yorumlayıcıda çalıştırır.

> [!Tip]
> Etkileşimli **pencere,** çevresindeki bir kapsama ait olan deyimleri otomatik olarak girintileerek normal Python komut satırı REPL deneyimini iyiler. Geçmişi (yukarı okla geri çağrılır) çok satırlı öğeler de sağlarken, komut satırı REPL yalnızca tek satır sağlar.

<a name="meta-commands"></a> Etkileşimli **pencere** çeşitli meta komutları da destekler. Tüm meta komutlar ile başlar ve yazarak meta komutların listesini ve belirli bir komutun kullanım `$` `$help` ayrıntılarını `$help <command>` edinebilirsiniz.

:::moniker range="<=vs-2017"

| Meta komutu | Açıklama |
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

| Meta komutu | Açıklama |
| --- | --- |
| `$$` | Oturum boyunca kod açıklaması yapmak için yararlı olan bir açıklama ekler. |
| `$cls`, `$clear` | Geçmiş ve yürütme bağlamını olduğu gibi bırakarak düzenleyici penceresinin içeriğini temizler. |
| `$help` | Komutların listesini veya belirli bir komutla ilgili yardımı görüntüleme. |
| `$load` | Dosyadan komutları yükler ve tamamlayana kadar yürütülür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına geçiştir. |
| `$reset` | Yürütme ortamını başlangıç durumuna sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

:::moniker-end

Komutlar, uygulama ve dışarı aktarma Visual Studio tarafından da genişletilebilir `IInteractiveWindowCommand` ([örnek).](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)

## <a name="switch-scopes"></a>Kapsamları değiştirme

Varsayılan olarak, **bir** projenin Etkileşimli penceresinin kapsamı, komut isteminden çalıştırmış gibi projenin başlangıç dosyası olarak gösterilir. Tek başına bir dosya için bu dosyanın kapsamını belirtir. Ancak REPL oturumunuz sırasında herhangi bir zamanda Etkileşimli pencerenin üst kısmında yer alan açılan menü **kapsamı** değiştirmenizi sağlar:

![Etkileşimli penceresi kapsamları](media/interactive-scopes.png)

Bir modülü (yazma gibi) içeri aktardıktan sonra, bu modülde herhangi bir kapsama `import importlib` geçmek için açılan açılır liste seçenekleri görüntülenir. Etkileşimli pencereye **gelen** bir ileti yeni kapsamı da gösterir, böylece oturumunuz sırasında belirli bir durumuna nasıl varmanızı izleyebilirsiniz.

Bir `dir()` kapsama girerek işlev adları, sınıflar ve değişkenler de dahil olmak üzere bu kapsamda geçerli tanımlayıcılar görüntülenir. Örneğin, ve `import importlib` ardından kullanılarak `dir()` aşağıdakiler gösterir:

![Etkileşimli penceresi kapsamına alma](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli'ye gönder komutu

Doğrudan Etkileşimli pencere içinde çalışmaya **ek** olarak düzenleyicide kod seçebilir, sağ  tıklar ve Etkileşimliye Gönder'i seçebilir veya Ctrl Enter **tuşuna** + **basabilirsiniz.**

![Etkileşimli menüye gönder komutu](media/interactive-send-to.png)

Bu komut, kodunuzu geliştirirken test etmek de dahil olmak üzere, iterative veya evrimsel kod geliştirme için yararlıdır. Örneğin Etkileşimli pencereye bir kod parçası göndererek çıkışını gördükte yukarı oka basarak kodu yeniden gösterebilir, değiştirebilir ve **Ctrl** Enter tuşlarına basarak hızlı bir şekilde test etmek için yukarı oka  + **basabilirsiniz.** **(Girişin** sonunda Enter tuşuna basılarak yürütülür, ancak girişin **ortasındaki Enter** tuşuna basılarak bir yeni satır ekler.) Koda sahip olduktan sonra kolayca proje dosyanıza kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual Studio ve **>>>** **...** RePL, Etkileşimli penceresinden düzenleyiciye **kod yapıştırıyorken** istemler. Yapıştır rePL istemlerini kaldırır **seçeneğini** kullanarak Araçlar Seçenekler Metin Düzenleyici  >    >    >  **Python**  >   Gelişmiş sekmesinde bu **davranışı değiştirebilirsiniz.** Bkz. [Seçenekler - Çeşitli seçenekler.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleri ile çalışma

Kod hücreleri veri analizinde kullanılabilir ve çeşitli metin düzenleyicileri tarafından de destekler.

Örneğin, bir kod dosyasını karalama defteri olarak kullanırken genellikle aynı anda göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplayarak kodu kod  hücresi olarak işaretlemek için hücrenin başına bir açıklama ekleyerek bir öncekini sona `#%%` erer. Kod hücreleri daraltılmış ve genişletilebilir ve bir kod hücresinde **Ctrl** Enter tuşlarıyla hücrenin tamamı Etkileşimli pencereye gönderilir ve bir +  sonrakine  taşınır.

Visual Studio, jupyter not defterini Python dosyası olarak dışarı aktarıyorsanız elde edersiniz biçimi gibi açıklamalarla başlayan kod `# In[1]:` hücrelerini de algılar. Bu algılama, Python dosyası olarak indirerek [Azure Notebooks](https://notebooks.azure.com/) bir not defterini çalıştırmayı, Visual Studio açma ve her hücreyi çalıştırmak için **Ctrl** Enter tuşlarını +  kullanarak çalıştırmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

Etkileşimli **pencere,** IntelliSense'in yalnızca kaynak kod analizini temel alan kod düzenleyicisinin aksine canlı nesneleri temel alan IntelliSense'i içerir. Bu öneriler, özellikle de dinamik **olarak oluşturulan** kodlarla Etkileşimli penceresinde daha doğrudur. Dezavantajı, yan etkilere sahip işlevlerin (günlüğe kaydetme iletileri gibi) geliştirme deneyiminizi etkileyemelerindendir.

Bu davranış bir sorunsa, Tamamlama Modu grubunda Araçlar **Seçenekleri** Python Etkileşimli Pencereleri altındaki ayarları Seçenekler - Etkileşimli pencereler seçenekleri altında açıklandığı  >    >    >   [gibi değiştirin.](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options) 
