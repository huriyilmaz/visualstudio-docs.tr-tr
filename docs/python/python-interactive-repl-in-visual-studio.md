---
title: Python etkileşimli penceresi (REPL)
description: Hızlı Python kodu geliştirme için etkileşimli pencereyi (REPL) Visual Studio.
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
ms.openlocfilehash: 36d9dfe9f7c986e46dad0708b2dad0ffd21c326ccaa466e8d90249bdc6d0941f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121367956"
---
# <a name="work-with-the-python-interactive-window"></a>Python Etkileşimli penceresi

Visual Studio Python ortamlarınızı her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar.  Bu pencere, komutpython.exerepl ile elde edersiniz. Etkileşimli **pencere** (Diğer Öğeleri Görüntüle **ve** Windows ortam Etkileşimli menü komutlarıyla açılır), rastgele Python kodu girmenize ve anında  >    >  sonuçları görmenize olanak **&lt; &gt;** sağlar. Bu kodlama yolu, API'leri ve kitaplıkları öğrenmenize, denemenize ve projelerinize dahil etmek için etkileşimli olarak çalışma kodu geliştirmenize yardımcı olur.

![Python etkileşimli penceresi](media/interactive-window.png)

Visual Studio bir dizi Python REPL modu vardır:

| Çoğaltma | Açıklama | Düzenleme | Hata Ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, Python ile doğrudan konuşma | Standart düzenleme (çok satırlı vb.). | Evet, aracılığıyla `$attach` | Hayır |
| Hata Ayıklama | Varsayılan REPL, hata ayıklamalı Python işlemiyle konuşma | Standart düzenleme | Yalnızca hata ayıklama | Hayır |
| IPython | REPL, IPython arka ucuyla sohbet ediyor | IPython komutları, Pylab kolaylıkları | Hayır | Evet, REPL'de satır içi |
| Pylab ile IPython | REPL, IPython arka ucuyla sohbet ediyor | Standart IPython | Hayır | Evet, ayrı pencere |

Bu makalede Standart ve **HATA AYıKLAMA** **REPL** modları açıklanmıştır. IPython modları hakkında ayrıntılı bilgi için [bkz. IPython REPL'yi kullanma.](interactive-repl-ipython.md)

Ctrl Enter gibi düzenleyiciyle etkileşimler de dahil olmak üzere örneklerle ayrıntılı bir kılavuz için + bkz. [Öğretici 3. Adım: Etkileşimli REPL penceresini kullanma.](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="open-an-interactive-window"></a>Bir Etkileşimli penceresi

Bir ortam için Etkileşimli pencereyi **açmanın** birkaç yolu vardır.

İlk olarak Python Ortamları penceresine **(**  >  Python **Ortamlarını Windows**  >  **Veya** **Ctrl** + **K**  >  **Ctrl**) + **`**  ve seçili ortam için Etkileşimli Pencere Aç komutunu veya düğmesini seçin.

![Python Ortamları penceresindeki Etkileşimli Pencere bağlantısı](media/interactive-window-opening.png)

İkincisi, Diğer Öğeleri Görüntüle  >  **menüsünün Windows** yakın bir yerde varsayılan ortamınız için **bir Python Etkileşimli** Pencere komutu  ve Ortamlar penceresine geçiş komutu vardır:

![Görünüm'de Etkileşimli Pencere menü öğeleri > Diğer Windows](media/interactive-window-menu.png)

Üçüncüsü, Projenizin  başlangıç dosyasında veya tek başına bir dosya   >  **\<Project | File> için, Python Etkileşimli'de** Yürüt'te Hata Ayıkla menü komutunu (**Shift** + **Alt** F5) seçerek etkileşimli bir pencere + **açabilirsiniz:**

![Python Project menüsünde yürütme](media/interactive-execute-project.png)

Son olarak, dosyada kod seçerek aşağıda açıklanan [ **Etkileşimliye Gönder komutunu**](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli penceresi seçenekleri

Araçlar Seçenekler  Python Interactive Windows aracılığıyla Etkileşimli pencerenin çeşitli yönlerini kontrol  >    >    >  **Windows** (bkz. [Seçenekler):](python-support-options-and-settings-in-visual-studio.md)

![Python etkileşimli pencere seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli penceresi

Etkileşimli **pencere** açıldıktan sonra, komut isteminde satır satır kod girmeye **\>\>\>** başlayabilirsiniz. Etkileşimli **pencere,** her satırı siz girerken yürütür. Bu satırda modülleri içeri aktarma, değişkenleri tanımlama gibi birçok işlem bulunur:

![Python etkileşimli penceresi](media/interactive-window.png)

Bunun istisnası, tam bir deyim yapmak için ek kod satırları gerektiğinde (örneğin, bir deyimin yukarıda gösterildiği gibi iki nokta `for` üst üste ile bitdiğinde) olduğudur. Bu durumlarda, yukarıdaki grafikte dördüncü ve beşinci satırlarda gösterildiği gibi satır istemi **...** olarak değişir ve bu da blok için ek satırlar girmeniz gerektiğini ifade ediyor. Boş bir **satırda Enter** tuşuna **basıyorsanız Etkileşimli** pencere bloğu kapatır ve yorumlayıcıda çalıştırır.

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

Komutlar, uygulama ve dışarı aktarma Visual Studio tarafından da genişletilebilir `IInteractiveWindowCommand` ([örneğin).](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)

## <a name="switch-scopes"></a>Kapsamları değiştirme

Varsayılan olarak, **bir** projenin Etkileşimli penceresinin kapsamı, komut isteminden çalıştırmış gibi projenin başlangıç dosyası olarak gösterilir. Tek başına bir dosya için bu dosyanın kapsamını belirtir. Ancak REPL oturumunuz sırasında herhangi bir zamanda Etkileşimli pencerenin üst kısmında yer alan açılan menü **kapsamı** değiştirmenizi sağlar:

![Etkileşimli penceresi kapsamları](media/interactive-scopes.png)

Bir modülü (örneğin, yazarak) içeri aktardıktan sonra, bu modülde herhangi bir kapsama geçmek `import importlib` için açılan açılır liste seçenekleri görüntülenir. Etkileşimli pencereye **gelen** bir ileti yeni kapsamı da gösterir, böylece oturumunuz sırasında belirli bir durumuna nasıl varmanızı izleyebilirsiniz.

Bir `dir()` kapsama girerek işlev adları, sınıflar ve değişkenler de dahil olmak üzere bu kapsamda geçerli tanımlayıcılar görüntülenir. Örneğin, ve `import importlib` ardından kullanılarak `dir()` aşağıdakiler gösterir:

![Etkileşimli penceresi kapsamına alma](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli'ye gönder komutu

Doğrudan Etkileşimli pencere içinde çalışmaya **ek** olarak düzenleyicide kod seçebilir, sağ  tıklar ve Etkileşimliye Gönder'i seçebilir veya Ctrl Enter **tuşuna** + **basabilirsiniz.**

![Etkileşimli menüye gönder komutu](media/interactive-send-to.png)

Bu komut, kodunuzu geliştirirken test etmek de dahil olmak üzere, iterative veya evrimsel kod geliştirme için yararlıdır. Örneğin Etkileşimli pencereye bir kod parçası göndererek çıkışını gördükte yukarı oka basarak kodu yeniden gösterebilir, değiştirebilir ve **Ctrl** Enter tuşlarına basarak kodu hızlıca  + **testebilirsiniz.** **(Girişin** sonunda Enter tuşuna basılarak yürütülür, ancak girişin **ortasındaki Enter** tuşuna basılarak bir yeni satır ekler.) Koda sahip olduktan sonra kolayca proje dosyanıza kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual Studio ve **>>>** **...** REPL, Etkileşimli penceresinden düzenleyiciye **kod yapıştırıyorken** istemler. Yapıştır rePL istemlerini kaldırır **seçeneğini** kullanarak Araçlar Seçenekler Metin Düzenleyici  >    >    >  **Python**  >   Gelişmiş sekmesinde bu **davranışı değiştirebilirsiniz.** Bkz. [Seçenekler - Çeşitli seçenekler.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleri ile çalışma

Kod hücreleri veri analizinde kullanılabilir ve çeşitli metin düzenleyicileri tarafından de destekler.

Örneğin, bir kod dosyasını karalama defteri olarak kullanırken genellikle aynı anda göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplayarak kodu kod  hücresi olarak işaretlemek için hücrenin başına bir açıklama ekleyerek bir öncekini sona `#%%` erer. Kod hücreleri daraltılmış ve genişletilebilir ve bir kod hücresinde **Ctrl** Enter tuşlarıyla hücrenin tamamı Etkileşimli pencereye gönderilir ve bir +  sonrakine  taşınır.

Visual Studio, jupyter not defterini Python dosyası olarak dışarı aktararak elde edersiniz gibi açıklamalarla başlayan kod hücrelerini `# In[1]:` de algılar. Bu algılama, Python dosyası olarak indirerek [Azure Notebooks](https://notebooks.azure.com/) bir not defterini çalıştırmayı, Visual Studio açma ve her hücreyi çalıştırmak için **Ctrl** Enter tuşlarını +  kullanarak çalıştırmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

Etkileşimli **pencere,** IntelliSense'in yalnızca kaynak kod analizini temel alan kod düzenleyicisinin aksine canlı nesneleri temel alan IntelliSense'i içerir. Bu öneriler, özellikle dinamik olarak **oluşturulan** kodlar için Etkileşimli pencerede daha doğrudur. Dezavantajı, yan etkilere sahip işlevlerin (günlüğe kaydetme iletileri gibi) geliştirme deneyiminizi etkileyemesidir.

Bu davranış bir sorunsa, Seçenekler - Etkileşimli pencereler seçenekleri altında açıklandığı Windows Tamamlama Modu grubunda Araçlar Seçenekleri Python Interactive Windows altındaki  >    >    >   [ayarları değiştirin.](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options) 
