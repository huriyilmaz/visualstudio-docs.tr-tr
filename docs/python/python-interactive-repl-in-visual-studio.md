---
title: Python etkileşimli penceresinde (REPL)
description: Visual Studio'da hızlı Python kodu geliştirmeye yönelik etkileşimli pencere (REPL) kullanın.
ms.date: 02/11/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 7ceecffec577528484cd67fd13d3e04f368fb916
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409976"
---
# <a name="work-with-the-python-interactive-window"></a>Python etkileşimli pencere ile çalışma

Visual Studio, Python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar. Bu, komut satırında *Python. exe* Ile aldığınız REPL 'u geliştirir. **Etkileşimli** pencere **( > ** **diğer Windows** >  **&lt;ortamı ile açılır&gt; etkileşimli** menü komutları), rastgele Python kodu girmenize ve anında sonuçları görmenizi sağlar. Öğrenin ve API'ları ve kitaplıkları ile etkileşimli çalışan kod projelerinizde geliştirmek için deneme bu şekilde kodlama yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio Python REPL modları, aralarından seçim yapabileceğiniz birçok vardır:

| REPL | Açıklama | Düzenleme | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, doğrudan Python konuştuğunu | Standart düzenleme (çok satırlı, vb.). | Evet, `$attach` aracılığıyla | Hayır |
| Hata ayıklama | Varsayılan REPL, hataları ayıklanan Python işlem konuştuğunu | Standart düzenleme | Yalnızca hata ayıklama | Hayır |
| Ipython | REPL, Ipython arka ucuna hakkında konuşuyor | Ipython komutları Pylab kolaylığı | Hayır | Evet, satır içi olarak REPL |
| Ipython Pylab olmadan | REPL, Ipython arka ucuna hakkında konuşuyor | Standart Ipython | Hayır | Evet, pencere ayırın |

Bu makalede, **Standart** ve **hata ayıklama** REPL modları açıklanır. IPython modlarında Ayrıntılar için bkz. [ıPYTHON REPL kullanma](interactive-repl-ipython.md).

Düzenleyiciyle ilgili, **Ctrl** **+gibi**bir kılavuz içeren ayrıntılı bir anlatım Için, bkz. [Adım 3: etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Etkileşimli bir pencere açın

Bir ortamın **etkileşimli** penceresini açmak için birkaç yol vardır.

İlk olarak, Python ortamları penceresine geçiş yapın ( **diğer Windows** > **Python ortamlarını** > **görüntüleyin** veya **CTRL**+**K** > **CTRL**+ **`** ) ve seçilen bir ortam için **etkileşimli pencere aç** komutunu veya düğmesini seçin.

![Python ortamları penceresinde etkileşimli penceresi bağlantı](media/interactive-window-opening.png)

İkinci olarak, > **görünümün** **diğer Windows** menüsünün alt kısmına yakın bir şekilde, varsayılan ortamınız Için bir **Python etkileşimli pencere** komutu ve **ortamlar** penceresine geçiş yapmak için bir komut vardır:

![Etkileşimli pencere menüsü öğelerini Görünüm > diğer Windows](media/interactive-window-menu.png)

Üçüncü olarak, projenizdeki başlangıç dosyasında veya tek başına bir dosya Için, **hata ayıkla** >  **\<projesi Yürüt ' i seçerek etkileşimli bir pencere açabilirsiniz. Python etkileşimli menü komutunda Dosya >** (**SHIFT**+**alt**+**F5**):

![Python etkileşimli menüde proje yürütülemiyor](media/interactive-execute-project.png)

Son olarak, dosyadaki kodu seçebilir ve aşağıda açıklanan [ **etkileşimli gönder** komutunu](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli pencere seçenekleri

**Etkileşimli pencerenin çeşitli** yönlerini **, >  > ** **Python** > **etkileşimli pencereler** aracılığıyla denetleyebilir (bkz. [Seçenekler](python-support-options-and-settings-in-visual-studio.md)):

![Python etkileşimli penceresinde seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli penceresini kullanma

**Etkileşimli** pencere açıldıktan sonra, **\>\>\>** istem satırına kod satırı satırı girmeye başlayabilirsiniz. **Etkileşimli** pencere, bunları girerken, modülleri içeri aktarma, değişkenleri tanımlama gibi her satırı yürütür:

![Python etkileşimli penceresi](media/interactive-window.png)

Bunun istisnası, bir `for` deyimin yukarıda gösterildiği gibi iki nokta üst üste ile sona erdiği gibi, bir deyimin daha fazla satır olması için gereken ek kod satırlarına ihtiyaç duymalıdır. Bu durumlarda, satır istemi, yukarıdaki grafiğin dördüncü ve beşinci satırlarında gösterildiği gibi, blok için ek satırlar girmeniz gerektiğini belirten **..** . olarak değişir. Boş bir satırda **ENTER** tuşuna bastığınızda **etkileşimli** pencere engellemeyi kapatır ve yorumlayıcı içinde çalıştırır.

> [!Tip]
> **Etkileşimli** pencere, kendisini çevreleyen bir kapsama ait deyimleri otomatik olarak girintileyerek olağan Python komut satırı REPL deneyiminden gelişir. Komut satırı REPL yalnızca tek satır sağlar (yukarı ok ile geri) buna ait geçmişi çok satırlı öğeleri de sağlar.

<a name="meta-commands"></a>**Etkileşimli** pencere ayrıca çeşitli meta komutları destekler. Tüm meta komutları `$`başlar ve belirli bir komutun kullanım ayrıntılarını almak üzere meta komutların ve `$help <command>` bir listesini almak için `$help` yazabilirsiniz.

| Meta komutu | Açıklama |
| --- | --- |
| `$$` | Oturumunuz boyunca açıklama kodu için yardımcı olan bir yorum ekler. |
| `$attach` | Visual Studio hata ayıklayıcı, hata ayıklamayı etkinleştirmek için REPL penceresi işleme ekler. |
| `$cls`, `$clear` | Geçmiş ve yürütme bağlamı dokunmadan Düzenleyicisi penceresinin içeriğini temizler. |
| `$help` | Komutların bir listesini görüntülemek veya belirli bir komut hakkında Yardım. |
| `$load` | Komut dosyasını yükler ve tamamlanana kadar yürütür. |
| `$mod` | Geçerli kapsam için belirtilen modül adı geçer. |
| `$reset` | Yürütme ortamını ilk durumuna sıfırlar, ancak geçmişini tutar. |
| `$wait` | En az belirtilen sayıda milisaniye bekler. |

Komutlar Ayrıca Visual Studio uzantıları tarafından `IInteractiveWindowCommand` ([örnek](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)) uygulayarak ve dışarı aktarılırken de genişletilebilir.

## <a name="switch-scopes"></a>Kapsamları geçiş

Varsayılan olarak, bir proje için **etkileşimli** pencere, komut isteminden çalıştırmanızdan sonra projenin başlangıç dosyası kapsamına alınır. Tek başına bir dosya için dosya kapsamları. Ancak, REPL oturumunuz sırasında dilediğiniz zaman, **etkileşimli** pencerenin üst kısmındaki açılan menü, kapsamı değiştirmenize izin verir:

![Etkileşimli pencere kapsamları](media/interactive-scopes.png)

`import importlib`yazma gibi bir modülü içeri aktardıktan sonra, bu modüldeki herhangi bir kapsama geçiş yapmak için seçenekler açılır. **Etkileşimli** penceredeki bir ileti de yeni kapsamı gösterir, bu sayede oturumunuz sırasında belirli bir duruma nasıl geldiğinizi izleyebilirsiniz.

Bir kapsama `dir()` girildiğinde, bu kapsamdaki işlev adları, sınıflar ve değişkenler dahil geçerli tanımlayıcılar görüntülenir. Örneğin, `dir()` tarafından izlenen `import importlib` kullanımı şunları gösterir:

![Etkileşimli pencerede importlib kapsamı](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli komutu Gönder

**Etkileşimli** pencere içinde doğrudan çalışmaya ek olarak, düzenleyicide kod seçebilir, sağ tıklayıp **etkileşimli olarak gönder** ' i seçebilir veya **ENTER** **tuşuna basarak**+.

![Etkileşimli bir menü komutu için Gönder](media/interactive-send-to.png)

Bu komut, geliştirirken kodunuzu test de dahil olmak üzere, yinelemeli veya gelişime kod geliştirme için yararlıdır. Örneğin, **etkileşimli** pencereye bir kod parçası gönderdikten ve çıkışını gördüğünüze sonra, kodu yeniden göstermek için yukarı oka basabilir, değiştirebilir ve **CTRL**+**ENTER**tuşlarına basarak hızlıca test edebilirsiniz. (Girişin sonunda **ENTER** tuşuna basmak bunu yürütür, ancak girişin ortasında **ENTER** tuşuna basıldığında yeni bir satır eklenir.) İstediğiniz koda sahip olduktan sonra proje dosyanıza tekrar kolayca kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual Studio **>>>** kaldırır ve **...** REPL **etkileşimli** pencereden düzenleyiciye kod yapıştırırken REPL istemleri. Bu davranışı **araçlar** > **Seçenekler** > **metin Düzenleyicisi** > **Python** > **Gelişmiş** sekmesinde, **Yapıştır REPL istemlerini kaldırır** seçeneğini kullanarak değiştirebilirsiniz. Bkz. [Seçenekler-çeşitli seçenekler](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleriyle çalışma

Kod hücreleri, veri çözümlemede kullanılabilir ve çeşitli metin düzenleyicileri tarafından desteklenir.

Örneğin, bir kod dosyasını karalama paneli olarak kullanırken, genellikle tümünü tek seferde göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplandırmak için, hücrenin başına `#%%` başlayarak bir açıklama ekleyerek kodu bir *kod hücresi* olarak işaretleyin, bu da öncekini sonlandırır. Kod hücreleri daraltılabilse ve genişletilebilir ve bir kod hücresinin içine **Ctrl**+**ENTER** kullanılması, tüm hücrenin **etkileşimli** pencereye gönderilir ve bir sonrakine gider.

Visual Studio Ayrıca, bir Jupyter Not defterini Python dosyası olarak dışa aktarırken alacağınız biçim olan `# In[1]:`gibi açıklamalarla başlayan kod hücrelerini algılar. Bu algılama, bir Python dosyası olarak indirerek, Visual Studio 'da açarak ve her hücreyi çalıştırmak için **Ctrl**+**ENTER** kullanarak [Azure Notebooks](https://notebooks.azure.com/) bir not defterini çalıştırmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

**Etkileşimli** pencere, IntelliSense 'in yalnızca kaynak kodu analizini temel alan kod düzenleyiciden farklı olarak, canlı nesneleri temel alan IntelliSense 'i içerir. Bu öneriler, özellikle dinamik olarak üretilen kodla **etkileşimli** pencerede daha doğrudur. (Örneğin, günlük iletilerini) yan etkileri olan işlevlere geliştirme deneyiminizi etkileyebilir dezavantajı olmasıdır.

Bu davranış bir sorun ise, [Seçenekler etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)' nde açıklandığı gibi, **araç** > **Seçenekler** > **Python** > , **tamamlama modu** grubundaki **etkileşimli pencereler** ' in altındaki ayarları değiştirin.
