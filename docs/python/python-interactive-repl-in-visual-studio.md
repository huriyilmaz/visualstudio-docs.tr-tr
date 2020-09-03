---
title: Python etkileşimli penceresi (REPL)
description: Visual Studio 'da hızlı Python kod geliştirme için etkileşimli pencereyi (REPL) kullanın.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 9608f273683865be767a44dd8f1d66106b97b7e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85533555"
---
# <a name="work-with-the-python-interactive-window"></a>Python etkileşimli penceresiyle çalışma

Visual Studio, Python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar. Bu, komut satırında *python.exe* Ile aldığınız REPL üzerinde iyileşir. **Etkileşimli** pencere ( **View**  >  **diğer Windows**  >  ** &lt; ortamını görüntüle &gt; etkileşimli** menü komutlarıyla açılır), rastgele Python kodu girmenizi ve anında sonuçları görmenizi sağlar. Bu kodlama yöntemi, API 'Leri ve kitaplıkları öğrenmenize ve denemenize ve etkileşimli olarak, projelerinize dahil etmek üzere çalışma kodu geliştirmenize yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio 'nun aralarından seçim yapabileceğiniz çeşitli Python REPL modları vardır:

| REPL | Description | Düzenleniyor | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, Python 'a doğrudan konuşuyor | Standart Düzen (çok satırlı, vb.). | Evet, ile `$attach` | No |
| Hata ayıklama | Varsayılan REPL, hata ayıklamanın Python işlemini | Standart Düzen | Yalnızca hata ayıklama | No |
| IPython | REPL, IPython arka ucu ile konuşuyor | IPython komutları, Pylab kolaylığı | No | Evet, REPL içinde satır içi |
| IPython w/o Pylab | REPL, IPython arka ucu ile konuşuyor | Standart IPython | No | Evet, pencereyi ayır |

Bu makalede, **Standart** ve **hata ayıklama** REPL modları açıklanır. IPython modlarında Ayrıntılar için bkz. [ıPYTHON REPL kullanma](interactive-repl-ipython.md).

Düzenleyiciyle ilgili, **CTRL tuşuna**da benzer yönergeler de dahil olmak üzere ayrıntılı bir + **Enter**kılavuz için bkz. [Adım 3: etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Etkileşimli pencere aç

Bir ortamın **etkileşimli** penceresini açmak için birkaç yol vardır.

İlk olarak, Python ortamları penceresine geçin (**View**  >  **diğer Windows**  >  **Python ortamlarını** veya **CTRL** + **K**  >  **CTRL**'i görüntüleyin + **`** ) ve seçilen bir ortam için **etkileşimli pencere aç** komutunu veya düğmesini seçin.

![Python ortamları penceresinde etkileşimli pencere bağlantısı](media/interactive-window-opening.png)

İkincisi, diğer pencereleri **görüntüle**menüsünün alt kısmına yakın bir şekilde,  >  **Other Windows** varsayılan ortamınız için bir **Python etkileşimli pencere** komutu ve **ortamlar** penceresine geçiş yapmak için bir komut vardır:

![Görünümdeki etkileşimli pencere menüsü öğeleri diğer pencereleri >](media/interactive-window-menu.png)

Üçüncü olarak, bir **etkileşimli** pencereyi projenizdeki başlangıç dosyasında ya da tek başına bir dosya için, **Debug**  >  ** \<Project | File> Python etkileşimli Çalıştır** menü komutunda hata ayıkla (**SHIFT** + **alt** + **F5**) seçerek açabilirsiniz:

![Projeyi Python etkileşimli menüsünde Yürüt](media/interactive-execute-project.png)

Son olarak, dosyadaki kodu seçebilir ve aşağıda açıklanan [ **etkileşimli gönder** komutunu](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli pencere seçenekleri

**Araç**seçenekleri Python etkileşimli pencereler aracılığıyla **etkileşimli** pencerenin çeşitli yönlerini denetleyebilir  >  **Options**  >  **Python**  >  **Interactive Windows** (bkz. [Seçenekler](python-support-options-and-settings-in-visual-studio.md)):

![Python etkileşimli pencere seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli pencereyi kullanma

**Etkileşimli** pencere açıldıktan sonra, istem satırına kod satırı satırı girmeye başlayabilirsiniz **\>\>\>** . **Etkileşimli** pencere, bunları girerken, modülleri içeri aktarma, değişkenleri tanımlama gibi her satırı yürütür:

![Python etkileşimli penceresi](media/interactive-window.png)

Özel durum, bir `for` deyimin yukarıda gösterildiği gibi iki nokta üstüste de bittiği durumlar gibi, bir bütün bildiri oluşturmak için ek kod satırlarının gerekli olduğu durumdur. Bu durumlarda, satır istemi, yukarıdaki grafiğin dördüncü ve beşinci satırlarında gösterildiği gibi, blok için ek satırlar girmeniz gerektiğini belirten **..** . olarak değişir. Boş bir satırda **ENTER** tuşuna bastığınızda **etkileşimli** pencere engellemeyi kapatır ve yorumlayıcı içinde çalıştırır.

> [!Tip]
> **Etkileşimli** pencere, kendisini çevreleyen bir kapsama ait deyimleri otomatik olarak girintileyerek olağan Python komut satırı REPL deneyiminden gelişir. Geçmişi (Yukarı oklu geri çekilir), çok satırlı öğeler de sağlar, ancak komut satırı REPL yalnızca tek satır sağlar.

<a name="meta-commands"></a>**Etkileşimli** pencere ayrıca çeşitli meta komutları destekler. Tüm meta komutları ile başlar `$` ve `$help` meta komutlarının bir listesini almak ve `$help <command>` belirli bir komutun kullanım ayrıntılarını almak için yazabilirsiniz.

| Meta-komut | Description |
| --- | --- |
| `$$` | Oturumunuz genelinde kod yorumu için yararlı olan bir açıklama ekler. |
| `$attach` | Hata ayıklamayı etkinleştirmek için Visual Studio hata ayıklayıcısını REPL pencere sürecine iliştirir. |
| `$cls`, `$clear` | , Geçmiş ve yürütme bağlamından ayrılmadan düzenleyici penceresinin içeriğini temizler. |
| `$help` | Komutların bir listesini veya belirli bir komutla ilgili yardım 'ı görüntüler. |
| `$load` | Komutları dosyadan yükler ve tamamlanana kadar yürütülür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına geçirir. |
| `$reset` | Yürütme ortamını ilk durumuna sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

Komutlar Ayrıca Visual Studio uzantıları tarafından ve dışarı aktarılırken `IInteractiveWindowCommand` ([örnek](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)) genişletilebilir.

## <a name="switch-scopes"></a>Kapsamları Değiştir

Varsayılan olarak, bir proje için **etkileşimli** pencere, komut isteminden çalıştırmanızdan sonra projenin başlangıç dosyası kapsamına alınır. Tek başına bir dosya için BT kapsamları bu dosyaya yöneliktir. Ancak, REPL oturumunuz sırasında dilediğiniz zaman, **etkileşimli** pencerenin üst kısmındaki açılan menü, kapsamı değiştirmenize izin verir:

![Etkileşimli pencere kapsamları](media/interactive-scopes.png)

Yazma gibi bir modülü içeri aktardıktan sonra, `import importlib` Bu modüldeki herhangi bir kapsama geçiş yapmak için seçenekler açılan kutuda görünür. **Etkileşimli** penceredeki bir ileti de yeni kapsamı gösterir, bu sayede oturumunuz sırasında belirli bir duruma nasıl geldiğinizi izleyebilirsiniz.

`dir()`Bir kapsama girildiğinde, bu kapsamdaki işlev adları, sınıflar ve değişkenler dahil geçerli tanımlayıcılar görüntülenir. Örneğin, `import importlib` aşağıdaki tarafından kullanılması `dir()` aşağıdakileri gösterir:

![Importlib kapsamındaki etkileşimli pencere](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli komuta gönder

**Etkileşimli** pencere içinde doğrudan çalışmaya ek olarak, düzenleyicide kod seçebilir, sağ tıklayıp **etkileşimli olarak gönder** ' i seçebilir veya **CTRL**+ + **ENTER**tuşuna basabilirsiniz.

![Etkileşimli menü komutuna gönder](media/interactive-send-to.png)

Bu komut, siz kodunuzu geliştirirken test etme dahil olmak üzere yinelemeli veya evkor kod geliştirmesi için yararlıdır. Örneğin, **etkileşimli** pencereye bir kod parçası gönderdikten ve çıkışını gördüğünüze sonra, kodu yeniden göstermek için yukarı oka basabilir, değiştirebilir ve hızlı ENTER **tuşuna basarak hızlıca**test edebilirsiniz + **Enter**. (Girişin sonunda **ENTER** tuşuna basmak bunu yürütür, ancak girişin ortasında **ENTER** tuşuna basıldığında yeni bir satır eklenir.) İstediğiniz koda sahip olduktan sonra proje dosyanıza tekrar kolayca kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual Studio kaldırır **>>>** ve **..** . REPL **etkileşimli** pencereden düzenleyiciye kod yapıştırırken REPL istemleri. Bu davranışı **araç**  >  **seçenekleri**  >  **metin düzenleyici**  >  **Python**  >  **Gelişmiş** sekmesinde **Yapıştır REPL istemlerini kaldırır** seçeneğini kullanarak değiştirebilirsiniz. Bkz. [Seçenekler-çeşitli seçenekler](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleriyle çalışma

Kod hücreleri, veri çözümlemede kullanılabilir ve çeşitli metin düzenleyicileri tarafından desteklenir.

Örneğin, bir kod dosyasını karalama paneli olarak kullanırken, genellikle tümünü tek seferde göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplamak için, hücrenin başlangıcına başlayarak bir açıklama ekleyerek kodu bir *kod hücresi* olarak işaretleyin `#%%` , bu da öncekini sonlandırır. Kod hücreleri daraltılabilse ve genişletilebilir ve **Ctrl** + bir kod hücresinin içinde CTRL**ENTER** kullanılması, tüm hücreyi **etkileşimli** pencereye gönderir ve bir sonrakine gider.

Visual Studio `# In[1]:` , bir Jupyter Not defterini Python dosyası olarak dışa aktarırken aldığınız biçim olan gibi açıklamalarla başlayan kod hücrelerini de algılar. Bu algılama, Python dosyası olarak indirerek [Azure Notebooks](https://notebooks.azure.com/) bir not defterini çalıştırmayı, Visual Studio 'da açmayı ve her hücreyi çalıştırmak için **CTRL** + **ENTER** tuşunu kullanmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

**Etkileşimli** pencere, IntelliSense 'in yalnızca kaynak kodu analizini temel alan kod düzenleyiciden farklı olarak, canlı nesneleri temel alan IntelliSense 'i içerir. Bu öneriler, özellikle dinamik olarak üretilen kodla **etkileşimli** pencerede daha doğrudur. Dezavantajı, yan etkileri olan işlevlerin (örneğin, günlük mesajları) geliştirme deneyiminizi etkileyebileceğini unutmayın.

Bu davranış bir sorun ise, **Tools**  >  **Options**  >  **Python**  >  [Seçenekler etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)' nde açıklandığı gibi, **tamamlama modu** grubundaki Araçlar Seçenekler Python**etkileşimli pencereler** altındaki ayarları değiştirin.
