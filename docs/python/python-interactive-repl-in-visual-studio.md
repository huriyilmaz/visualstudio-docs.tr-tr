---
title: Python etkileşimli pencere (REPL)
description: Visual Studio'da hızlı Python kodu geliştirme için etkileşimli pencereyi (REPL) kullanın.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302765"
---
# <a name="work-with-the-python-interactive-window"></a>Python Interactive penceresi ile çalışma

Visual Studio, python ortamlarınızın her biri için etkileşimli bir okuma-değerlendirme-yazdırma döngüsü (REPL) penceresi sağlar ve komut satırında *python.exe* ile elde ettiğiniz REPL'yi geliştirir. **Etkileşimli** pencere **(Diğer Windows** > **&lt;&gt; ortamını** **Görüntüle** > Etkileşimli menü komutlarıyla açılır) rasgele Python kodu girmenizi ve hemen sonuçları görmenizi sağlar. Bu kodlama şekli, API'leri ve kitaplıkları öğrenmenize ve denemeler ilerlemenize ve projelerinize dahil etmek üzere etkileşimli olarak çalışma kodu geliştirmenize yardımcı olur.

![Python etkileşimli pencere](media/interactive-window.png)

Visual Studio arasında seçim yapmak için Python REPL modları bir dizi vardır:

| Çoğaltma | Açıklama | Düzenleme | Hata ayıklama | Görüntüler |
| --- | --- | --- | --- | --- |
| Standart | Varsayılan REPL, doğrudan Python ile konuşuyor | Standart düzenleme (çok satırlı, vb.). | Evet, üzerinden`$attach` | Hayır |
| Hata ayıklama | Varsayılan REPL, debugged Python işlemi için görüşmeler | Standart düzenleme | Yalnızca hata ayıklama | Hayır |
| IPython | IPython backend REPL görüşmeler | IPython komutları, Pylab kolaylıkları | Hayır | Evet, REPL içinde satır |
| IPython w / o Pylab | IPython backend REPL görüşmeler | Standart IPython | Hayır | Evet, ayrı pencere |

Bu **makalede, Standart** ve **Hata Ayıklama** REPL modları açıklanmaktadır. IPython modları hakkında ayrıntılı bilgi için Bkz. [IPython REPL'yi kullanın.](interactive-repl-ipython.md)

**Ctrl**+**Enter**gibi editörle etkileşimleri de dahil olmak üzere örnekleriçeren ayrıntılı bir gözden geçirme için [bkz.](tutorial-working-with-python-in-visual-studio-step-03-interactive-repl.md)

## <a name="open-an-interactive-window"></a>Etkileşimli pencere açma

**Etkileşimli** pencereyi bir ortam için açmanın birkaç yolu vardır.

İlk olarak, Python Ortamları penceresine **(Diğer Windows** > **Python Ortamlarını** **Görüntüle** > veya **Ctrl**+**K** > **Ctrl)**+**`** geçin ve seçilen bir ortam için **Etkileşimli Pencereyi Aç** komutunu veya düğmesini seçin.

![Python Ortamları penceresinde etkileşimli pencere bağlantısı](media/interactive-window-opening.png)

İkinci olarak,**Diğer Windows'u** **Görüntüle** > menüsünün alt kısmında varsayılan ortamınız için Python **Etkileşimli Pencere** komutunun yanı sıra **Ortamlar** penceresine geçmek için bir komut vardır:

![Diğer Windows'> Görünüm'deki Etkileşimli Pencere menü öğeleri](media/interactive-window-menu.png)

Üçüncü olarak, **Hata Ayıklama** > Yürütme **Interactive** ** \<Projesi 'ni seçerek projenizdeki başlangıç dosyasında veya tek başına bir dosya için Etkileşimli pencere açabilirsiniz | Python Interactive menü komutunda dosya>** (**Shift**+**Alt**+**F5**):

![Python Interactive menüsünde Project'i Yürüt](media/interactive-execute-project.png)

Son olarak, dosyadaki kodu seçebilir ve aşağıda açıklanan [ **Etkileşimli Gönder** komutunu](#send-to-interactive-command) kullanabilirsiniz.

## <a name="interactive-window-options"></a>Etkileşimli pencere seçenekleri

 >  **Araçlar** > **Seçenekleri** > **Python****İnteraktif Windows** aracılığıyla **Etkileşimli** pencerenin çeşitli yönlerini kontrol edebilirsiniz [(Seçenekler](python-support-options-and-settings-in-visual-studio.md)bakınız):

![Python etkileşimli pencere seçenekleri](media/options-interactive-windows.png)

## <a name="use-the-interactive-window"></a>Etkileşimli pencereyi kullanma

**Etkileşimli** pencere açıldıktan ** \> \> ** sonra, komut isteminde kod satır satır girmeye başlayabilirsiniz. **Etkileşimli** pencere, modülleri içe aktarmayı, değişkenleri tanımlamayı ve benzeri konuları içeren her satırı girerken yürütür:

![Python etkileşimli pencere](media/interactive-window.png)

Özel durum, tam bir deyim yapmak için ek kod satırlarına ihtiyaç duyulduğunda (örneğin, yukarıda gösterildiği gibi bir `for` nokta üst üste sona erdiğinde). Bu gibi durumlarda, satır istemi **...** yukarıdaki grafikte dördüncü ve beşinci satırlarda gösterildiği gibi, blok için ek satırlar girmeniz gerektiğini belirten değişir. Boş bir satırda **Enter** tuşuna bastığınızda, **Etkileşimli** pencere bloğu kapatır ve yorumlayıcıda çalıştırılır.

> [!Tip]
> **Etkileşimli** pencere, çevreleyen bir kapsama ait ifadeleri otomatik olarak girintisi yaparak her zamanki Python komut satırı REPL deneyimini geliştirir. Geçmişi (yukarı okla geri çağrıldı) çok satırlı öğeler de sağlarken, komut satırı REPL yalnızca tek satırlar sağlar.

<a name="meta-commands"></a>**Etkileşimli** pencere de birkaç meta komutları destekler. Tüm meta komutları `$`ile başlar ve `$help` meta komutların bir listesini almak `$help <command>` ve belirli bir komut için kullanım ayrıntılarını almak için yazabilirsiniz.

| Meta komut | Açıklama |
| --- | --- |
| `$$` | Oturumunuz boyunca kod hakkında yorum yapmak için yararlı olan bir yorum ekler. |
| `$attach` | Hata ayıklamayı etkinleştirmek için Visual Studio hata ayıklama işlemini REPL penceresi işlemine bağlar. |
| `$cls`, `$clear` | Düzenleyici penceresinin içeriğini temizler ve geçmiş ve yürütme bağlamını bozulmadan bırakır. |
| `$help` | Komutların listesini görüntüleyin veya belirli bir komutta yardım edin. |
| `$load` | Komutları dosyadan yükler ve tamamlanana kadar yürütür. |
| `$mod` | Geçerli kapsamı belirtilen modül adına değiştirir. |
| `$reset` | Yürütme ortamını ilk duruma sıfırlar, ancak geçmişi tutar. |
| `$wait` | En az belirtilen milisaniye sayısını bekler. |

Komutlar da uygulayarak ve dışa aktararak `IInteractiveWindowCommand` Visual Studio uzantıları tarafından genişletilebilir[(örnek).](https://github.com/Microsoft/PTVS/blob/master/Python/Product/PythonTools/PythonTools/Repl/InteractiveWindowCommands.cs#L85)

## <a name="switch-scopes"></a>Kapsamları değiştirme

Varsayılan olarak, bir proje için **Etkileşimli** pencere komut istemi nden çalıştırDığınız gibi projenin başlangıç dosyasına doğru kapsamlıdır. Tek başına bir dosya için, bu dosyaya kapsamı. Ancak, REPL oturumunuz sırasında istediğiniz zaman, **Etkileşimli** pencerenin üst kısmındaki açılır menü kapsamı değiştirmenize olanak tanır:

![Etkileşimli pencere kapsamları](media/interactive-scopes.png)

Yazma gibi bir modülü içe `import importlib`aktardıktan sonra, bu modüldeki herhangi bir kapsama geçmek için açılan yolda seçenekler görünür. **Etkileşimli** penceredeki bir ileti de yeni kapsamı gösterir, böylece oturumunuz sırasında belirli bir duruma nasıl vardığınızı izleyebilirsiniz.

Bir `dir()` kapsamda girilen işlev adları, sınıflar ve değişkenler de dahil olmak üzere bu kapsamda geçerli tanımlayıcılar görüntüler. Örneğin, aşağıdakileri `import importlib` `dir()` kullanarak aşağıdakileri gösterir:

![Importlib kapsamında etkileşimli pencere](media/interactive-importlib-scope.png)

## <a name="send-to-interactive-command"></a>Etkileşimli komuta gönder

**Doğrudan Etkileşimli** pencere içinde çalışmaya ek olarak, düzenleyicide kodu seçebilir, sağ tıklayabilir ve **Etkileşimli'ye Gönder'i** seçebilir veya **Ctrl**+**Enter**tuşuna basabilirsiniz.

![Etkileşimli menü komutuna gönder](media/interactive-send-to.png)

Bu komut, kodunuzu geliştirirken test etmek de dahil olmak üzere yinelemeli veya evrimsel kod geliştirme için yararlıdır. Örneğin, **Etkileşimli** pencereye bir kod parçası gönderdikten ve çıktısını gördükten sonra, kodu yeniden göstermek, değiştirmek ve **Ctrl**+**Enter**tuşuna basarak hızlı bir şekilde test etmek için yukarı oktuşuna basabilirsiniz. (Girişin sonunda **Enter** tuşuna basıldığında bunu yürütür, ancak girişin ortasında **Enter** tuşuna basArak yeni bir satır ekler.) İstediğiniz kodu aldıktan sonra, kolayca proje dosyanıza yeniden kopyalayabilirsiniz.

> [!Tip]
> Varsayılan olarak, Visual **>>>** Studio kaldırır ve **...** RePL, **Etkileşimli** pencereden düzenleyiciye kodu yapıştırırken ister. **Yapıştır REPL istemleri** seçeneğini kaldırarak **Araçlar** > **Seçenekleri** > Metin**Düzenleyicisi** > **Text Editor** > Python**Advanced** sekmesinde bu davranışı değiştirebilirsiniz. Bkz. [Seçenekler - Çeşitli seçenekler.](python-support-options-and-settings-in-visual-studio.md#miscellaneous-options)

<!-- After 15.3 is released, you can also press **Undo** after pasting to restore prompts. Press **Undo** a second time to remove the pasted code entirely. -->

## <a name="work-with-code-cells"></a>Kod hücreleriyle çalışma

Kod hücreleri veri analizinde kullanılabilir ve çeşitli metin düzenleyicileri tarafından desteklenir.

Örneğin, bir kod dosyasını karalama defteri olarak kullanırken, genellikle hepsini aynı anda göndermek istediğiniz küçük bir kod bloğuna sahip olursunuz. Kodu birlikte gruplandırmak için, *code cell* önceki hücreyi sona `#%%` erdirene hücrenin başına başlayan bir açıklama ekleyerek kodu kod hücresi olarak işaretleyin. Kod hücreleri daraltılabilir ve genişletilebilir ve **Ctrl**+**Enter'u** kullanarak bir kod hücresinin içine gir tüm **hücreetkileşimli** pencereye gönderir ve bir sonraki hücreye taşınır.

Visual Studio ayrıca Python dosyası olarak `# In[1]:`bir Jupyter not defteri dışa aktarırken aldığınız biçim gibi yorumlarla başlayan kod hücrelerini algılar. Bu algılama, Python dosyası olarak indirerek, Visual Studio'da açArak ve her hücreyi çalıştırmak için **Ctrl**+**Enter'u** kullanarak [Azure Not Defterleri'nden](https://notebooks.azure.com/) bir dizüstü bilgisayarı çalıştırmayı kolaylaştırır.

![Etkileşimli kod hücreleri](media/interactive-code-cells.png)

## <a name="intellisense-behavior"></a>IntelliSense davranışı

**Etkileşimli** pencere, IntelliSense'in yalnızca kaynak kod analizine dayandığı kod düzenleyicisinin aksine, canlı nesnelere dayalı IntelliSense'i içerir. Bu öneriler **Etkileşimli** pencerede, özellikle dinamik olarak oluşturulan kodda daha doğrudur. Dezavantajı yan etkileri olan işlevleri (günlük iletileri gibi) geliştirme deneyiminizi etkileyebilir.

Bu davranış bir sorunsa, [Seçenekler - Etkileşimli windows seçeneklerinde](python-support-options-and-settings-in-visual-studio.md#interactive-windows-options)açıklandığı gibi **Tamamlanma Modu** grubunda **Araçlar** > **Seçenekleri** > **Python** > **Interactive Windows** altındaki ayarları değiştirin.
