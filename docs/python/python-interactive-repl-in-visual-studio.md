---
title: Python etkileşimli penceresi (REPL)
description: Visual Studio ' de hızlı Python kod geliştirmesi için etkileşimli pencereyi (REPL) kullanın.
ms.date: 02/11/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: db046648d78caeb1ec779ae556709806d72dc55c
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726794"
---
# <a name="work-with-the-python-interactive-window"></a>Python etkileşimli penceresiyle çalışma

Visual Studio, Python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (repl) penceresi sağlar. bu, komut satırında *python.exe* sahip olduğunuz REPL üzerinde geliştirilir. **etkileşimli** pencere (   >  **diğer Windows**  >  **&lt; ortamı görüntüle &gt; etkileşimli** menü komutlarıyla açılır), rastgele Python kodu girmenizi ve anında sonuçları görmenizi sağlar. Bu kodlama yöntemi, API 'Leri ve kitaplıkları öğrenmenize ve denemenize ve etkileşimli olarak, projelerinize dahil etmek üzere çalışma kodu geliştirmenize yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio, aralarından seçim yapabileceğiniz bir dizi Python REPL moduna sahiptir:

| REPL | Description | Düzenleme | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, Python 'a doğrudan konuşuyor | Standart Düzen (çok satırlı, vb.). | Evet, ile `$attach` | No |
| Hata Ayıklama | Varsayılan REPL, hata ayıklamanın Python işlemini | Standart Düzen | Yalnızca hata ayıklama | No |
| IPython | REPL, IPython arka ucu ile konuşuyor | IPython komutları, Pylab kolaylığı | No | Evet, REPL içinde satır içi |
| IPython w/o Pylab | REPL, IPython arka ucu ile konuşuyor | Standart IPython | No | Evet, pencereyi ayır |

Bu makalede, **Standart** ve **hata ayıklama** REPL modları açıklanır. IPython modlarında Ayrıntılar için bkz. [ıPYTHON REPL kullanma](interactive-repl-ipython.md).

Düzenleyiciyle ilgili, **CTRL tuşuna** da benzer yönergeler de dahil olmak üzere ayrıntılı bir + kılavuz için bkz. [Adım 3: etkileşimli REPL penceresini kullanma](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md).

## <a name="open-an-interactive-window"></a>Etkileşimli pencere aç

Bir ortamın **etkileşimli** penceresini açmak için birkaç yol vardır.

ilk olarak, python ortamları penceresine geçiş yapın (  >  **diğer Windows**  >  **python ortamlarını** görüntüleyin veya **ctrl** tuşuna basın +   >   + **`** ) ve seçilen bir ortam için **etkileşimli pencere aç** komutunu veya düğmesini seçin.

![Python ortamları penceresinde etkileşimli pencere bağlantısı](media/interactive-window-opening.png)

ikincisi, diğer Windows **görüntüle** menüsünün alt kısmına yakın bir şekilde,  >   varsayılan ortamınız için bir **Python etkileşimli pencere** komutu ve **ortamlar** penceresine geçiş yapmak için bir komut vardır:

![Görünümdeki etkileşimli pencere menü öğeleri > diğer Windows](media/interactive-window-menu.png)

Üçüncü olarak, bir **etkileşimli** pencereyi projenizdeki başlangıç dosyasında ya da tek başına bir dosya için,   >  **\<Project | File> Python etkileşimli Çalıştır** menü komutunda hata ayıkla (**SHIFT** + **alt** + **F5**) seçerek açabilirsiniz:

![Python etkileşimli menüsünde Project yürütme](media/interactive-execute-project.png)

Son olarak, dosyadaki kodu seçebilir ve aşağıda açıklanan [ **etkileşimli gönder** komutunu](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli pencere seçenekleri

**araç** seçenekleri Python etkileşimli Windows aracılığıyla **etkileşimli** pencerenin çeşitli yönlerini denetleyebilirsiniz  >    >    >   (bkz. [seçenekler](python-support-options-and-settings-in-visual-studio.md)):

![Python etkileşimli pencere seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli pencereyi kullanma

**Etkileşimli** pencere açıldıktan sonra, istem satırına kod satırı satırı girmeye başlayabilirsiniz **\>\>\>** . **Etkileşimli** pencere, bunları girerken, modülleri içeri aktarma, değişkenleri tanımlama gibi her satırı yürütür:

![Python etkileşimli penceresi](media/interactive-window.png)

Özel durum, bir `for` deyimin yukarıda gösterildiği gibi iki nokta üstüste de bittiği durumlar gibi, bir bütün bildiri oluşturmak için ek kod satırlarının gerekli olduğu durumdur. Bu durumlarda, satır istemi, yukarıdaki grafiğin dördüncü ve beşinci satırlarında gösterildiği gibi, blok için ek satırlar girmeniz gerektiğini belirten **..** . olarak değişir. Boş bir satırda **ENTER** tuşuna bastığınızda **etkileşimli** pencere engellemeyi kapatır ve yorumlayıcı içinde çalıştırır.

> [!Tip]
> **Etkileşimli** pencere, kendisini çevreleyen bir kapsama ait deyimleri otomatik olarak girintileyerek olağan Python komut satırı REPL deneyiminden gelişir. Geçmişi (Yukarı oklu geri çekilir), çok satırlı öğeler de sağlar, ancak komut satırı REPL yalnızca tek satır sağlar.

<a name="meta-commands"></a>**Etkileşimli** pencere ayrıca çeşitli meta komutları destekler. Tüm meta komutları ile başlar `$` ve `$help` meta komutlarının bir listesini almak ve `$help <command>` belirli bir komutun kullanım ayrıntılarını almak için yazabilirsiniz.

:::moniker range="<=vs-2017"

| Meta-komut | Description |
| --- | --- |
| `$$` | Oturumunuz genelinde kod yorumu için yararlı olan bir açıklama ekler. |
| `$attach` | hata ayıklamayı etkinleştirmek için Visual Studio hata ayıklayıcısını REPL pencere işlemine iliştirir. |
| `$cls`, `$clear` | , Geçmiş ve yürütme bağlamından ayrılmadan düzenleyici penceresinin içeriğini temizler. |
| `$help` | Komutların bir listesini veya belirli bir komutla ilgili yardım 'ı görüntüler. |
| `$load` | Komutları dosyadan yükler ve tamamlanana kadar yürütülür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına geçirir. |
| `$reset` | Yürütme ortamını ilk durumuna sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

:::moniker-end

:::moniker range=">=vs-2019"

| Meta-komut | Description |
| --- | --- |
| `$$` | Oturumunuz genelinde kod yorumu için yararlı olan bir açıklama ekler. |
| `$cls`, `$clear` | , Geçmiş ve yürütme bağlamından ayrılmadan düzenleyici penceresinin içeriğini temizler. |
| `$help` | Komutların bir listesini veya belirli bir komutla ilgili yardım 'ı görüntüler. |
| `$load` | Komutları dosyadan yükler ve tamamlanana kadar yürütülür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına geçirir. |
| `$reset` | Yürütme ortamını ilk durumuna sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

:::moniker-end

komutlar ayrıca, uygulama ve dışa aktarma `IInteractiveWindowCommand` ([örnek](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)) tarafından Visual Studio uzantılarına göre genişletilebilir.

## <a name="switch-scopes"></a>Kapsamları Değiştir

Varsayılan olarak, bir proje için **etkileşimli** pencere, komut isteminden çalıştırmanızdan sonra projenin başlangıç dosyası kapsamına alınır. Tek başına bir dosya için BT kapsamları bu dosyaya yöneliktir. Ancak, REPL oturumunuz sırasında dilediğiniz zaman, **etkileşimli** pencerenin üst kısmındaki açılan menü, kapsamı değiştirmenize izin verir:

![Etkileşimli pencere kapsamları](media/interactive-scopes.png)

Yazma gibi bir modülü içeri aktardıktan sonra, `import importlib` Bu modüldeki herhangi bir kapsama geçiş yapmak için seçenekler açılan kutuda görünür. **Etkileşimli** penceredeki bir ileti de yeni kapsamı gösterir, bu sayede oturumunuz sırasında belirli bir duruma nasıl geldiğinizi izleyebilirsiniz.

`dir()`Bir kapsama girildiğinde, bu kapsamdaki işlev adları, sınıflar ve değişkenler dahil geçerli tanımlayıcılar görüntülenir. Örneğin, `import importlib` aşağıdaki tarafından kullanılması `dir()` aşağıdakileri gösterir:

![Importlib kapsamındaki etkileşimli pencere](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli komuta gönder

**Etkileşimli** pencere içinde doğrudan çalışmaya ek olarak, düzenleyicide kod seçebilir, sağ tıklayıp **etkileşimli olarak gönder** ' i seçebilir veya **CTRL**+ + **ENTER** tuşuna basabilirsiniz.

![Etkileşimli menü komutuna gönder](media/interactive-send-to.png)

Bu komut, siz kodunuzu geliştirirken test etme dahil olmak üzere yinelemeli veya evkor kod geliştirmesi için yararlıdır. Örneğin, **etkileşimli** pencereye bir kod parçası gönderdikten ve çıkışını gördüğünüze sonra, kodu yeniden göstermek için yukarı oka basabilir, değiştirebilir ve hızlı ENTER **tuşuna basarak hızlıca** test edebilirsiniz + . (Girişin sonunda **ENTER** tuşuna basmak bunu yürütür, ancak girişin ortasında **ENTER** tuşuna basıldığında yeni bir satır eklenir.) İstediğiniz koda sahip olduktan sonra proje dosyanıza tekrar kolayca kopyalayabilirsiniz.

> [!Tip]
> varsayılan olarak, Visual Studio kaldırılır **>>>** ve **...** REPL **etkileşimli** pencereden düzenleyiciye kod yapıştırırken REPL istemleri. Bu davranışı **araç**  >  **seçenekleri**  >  **metin düzenleyici**  >  **Python**  >  **Gelişmiş** sekmesinde **Yapıştır REPL istemlerini kaldırır** seçeneğini kullanarak değiştirebilirsiniz. Bkz. [Seçenekler-çeşitli seçenekler](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options).

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleriyle çalışma

Kod hücreleri, veri çözümlemede kullanılabilir ve çeşitli metin düzenleyicileri tarafından desteklenir.

Örneğin, bir kod dosyasını karalama paneli olarak kullanırken, genellikle tümünü tek seferde göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplamak için, hücrenin başlangıcına başlayarak bir açıklama ekleyerek kodu bir *kod hücresi* olarak işaretleyin `#%%` , bu da öncekini sonlandırır. Kod hücreleri daraltılabilse ve genişletilebilir ve  + bir kod hücresinin içinde CTRL **ENTER** kullanılması, tüm hücreyi **etkileşimli** pencereye gönderir ve bir sonrakine gider.

Visual Studio ayrıca `# In[1]:` , bir jupyter not defterini Python dosyası olarak dışa aktarırken aldığınız biçim olan gibi açıklamalarla başlayan kod hücrelerini de algılar. bu algılama, Python dosyası olarak indirerek [Azure Notebooks](https://notebooks.azure.com/) bir not defterini çalıştırmayı, Visual Studio açmayı ve her hücreyi çalıştırmak için **Ctrl** + **Enter** tuşunu kullanmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

**Etkileşimli** pencere, IntelliSense 'in yalnızca kaynak kodu analizini temel alan kod düzenleyiciden farklı olarak, canlı nesneleri temel alan IntelliSense 'i içerir. Bu öneriler, özellikle dinamik olarak üretilen kodla **etkileşimli** pencerede daha doğrudur. Dezavantajı, yan etkileri olan işlevlerin (örneğin, günlük mesajları) geliştirme deneyiminizi etkileyebileceğini unutmayın.

bu davranış bir sorun ise,   >    >    >  [seçenekler etkileşimli Windows seçenekleri](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)bölümünde açıklandığı gibi, **tamamlama modu** grubundaki araçlar seçenekler Python **etkileşimli Windows** altındaki ayarları değiştirin.
