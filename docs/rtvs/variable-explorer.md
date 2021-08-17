---
title: R için Değişken Gezgini
description: Visual Studio Değişken Gezgini, geçerli R oturumunda verilen bir kapsamdaki tüm değişkenleri gösterir.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: be6f619fc23db19b2342402a8b14fb190cbdc801
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060485"
---
# <a name="variable-explorer"></a>Değişken Gezgini

**Değişken Gezgini** penceresi, **r araçları**  >  **Windows**  >  **Değişken Gezgini** (veya  + **R Veri Bilimi Ayarları araçları**'nı kullandıysanız Ctrl **8** ) kullanılarak açılır  >  . geçerli R oturumunda belirli bir kapsamdaki tüm değişkenleri gösterir. Örneğin, **değişken Gezgini** açarsanız ve [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md)aşağıdaki satırları girerseniz:

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

**Değişken Gezgini** penceresi aşağıdaki gibi görünür:

![Visual Studio 'de değişken Gezgini penceresi](media/variable-explorer-window.png)

Oturumda tanımlanmış daha karmaşık bir R veri çerçevesine sahipseniz verilere gidebilirsiniz. Örneğin, çalıştırdıktan sonra, `cars <- mtcars` **değişken Gezgini** farklı düğümleri genişleterek veri kümesinde gezinebilirsiniz:

![Değişken Gezgini genişletilmiş görünümü](media/variable-explorer-expanded-results.png)

Değişkenleri silmek için sağ tıklayın ve **Sil**' i seçin ya da değişkeni seçip **Delete** tuşuna basın.

Ayrıca, artımlı arama kullanarak bir veri çerçevesindeki gözlemde arayabilirsiniz. İlk olarak, aramak istediğiniz veri çerçevesindeki düğümleri genişletin ve arama kutusuna arama terimlerini girin.

## <a name="details-table-view"></a>Ayrıntılar (tablo) görünümü

Veriler çoğunlukla tablo olarak olduğu için, büyüteç simgesini seçerek veya sağ tıklayıp **Ayrıntıları göster**' i seçerek herhangi bir karmaşık veri türünü ayrı bir tablo olarak görüntüleyebilirsiniz.

![Değişken Gezgini tablo görünümü](media/variable-explorer-table-view.png)

Sütun başlığına tıklanması verileri sütuna göre sıralar (artan ve azalan arasında değişen). **SHIFT** tuşunu basılı tutmak ve ek sütunlara tıklatmak, bu sütunları sıralamaya de ekler. **SHIFT** olmadan bir sütuna tıkladığınızda tek sütunlu sıralama döndürülür.

Sütun başlıklarını tıklamayı seçtiğiniz sıra, sıralamanın gerçekleştirileceği sırayı belirler. Örneğin, sağ **üst karakter** + sütununa  **tıklayın**  + ve sonra listeyi artan silindir ve azalan mil başına-galon için sıralamak üzere **MPG** sütununa iki kez **tıklayın** :

![İki sütuna göre veri sıralamanın tablo görünümü.](media/variable-explorer-table-view-sorting.png)

**Değişken Gezgini** ve tablo görünümleri ayrı Visual Studio pencerelerin içinde olduğundan, bunları yan yana çalışma için istediğiniz şekilde düzenleyebilirsiniz. genel yönergeler için [Visual Studio pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md) bölümüne bakın.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Excel (veya diğer CSV özellikli uygulama) içinde açın

Daha fazla düzenleme ve çözümleme için, oturum değişkenlerini CSV 'ye aktarmak genellikle yararlı olur. dışarı aktarma işlemi, Değişken Gezgini her bir düğümün yanındaki küçük Excel simgesiyle ( ![ Excel dışa aktarma simgesiyle ](media/variable-explorer-excel-icon.png) ) veya bir öğeye sağ tıklayıp **CSV uygulamasında aç**' ı seçerek yapılır. Simgenin seçilmesi, verileri *%userprofile%\Documents\ RTVS_CSV_Exports* klasöründe yenı bir CSV dosyasına yazar ve ardından bu dosyayı başlatır ve bu dosyayı başlatır ve *.csv* uzantısıyla ilişkili herhangi bir uygulamanın bulunduğu bu dosyayı açar.

## <a name="scopes"></a>Kapsamlar

Varsayılan olarak **değişken Gezgini** genel kapsama açılır. Pencerenin en üstündeki açılan listeden bir paket seçerek paket kapsamına geçebilirsiniz.

![Paket kapsamını gösteren değişken Gezgini](media/variable-explorer-package-scopes.png)

Ayrıca, hata ayıklayıcıdaki bir kesme noktasında durdurulduğunda bir işlev kapsamına geçiş yapabilirsiniz ( **değişken Gezgini** , hata ayıklanan kodun işlev kapsamına otomatik olarak geçmediğini unutmayın):

![Hata ayıklama sırasında bir veri çerçevesini göstermek Değişken Gezgini](media/variable-explorer-as-locals-window.png)

**Değişken Gezgini** , bir işlevdeki yerel değişkenleri gösterme gibi, hata ayıklayıcıdaki kodda adım adım iler, işlev kapsamını otomatik olarak değiştirir.

## <a name="import-data-into-variable-explorer"></a>Değişken Gezgini verileri içeri aktarma

**Değişken Gezgini** araç çubuğunda, **r araçları**  >  **verileri** menüsünde de kullanılabilen iki komut, dış CSV veri kümelerini r oturumunuza içeri aktarın: **veri kümesini Web URL 'sinden r oturumuna** aktar ve **veri kümesini metin dosyasından r oturumuna** aktar.

içeri aktarılacak CSV dosyasını tanımladıktan sonra Visual Studio, bu veri dosyasının nasıl ayrıştırılabileceğini (yani, alan ayırıcısının ne olduğu ve tekliflerin nasıl işleneceği) denetlemek için kullanabileceğiniz seçeneklere sahip bir **içeri aktarma veri kümesi** iletişim kutusu görüntüler. Ayrıca, içeri aktarılan veri çerçevesinin ve özgün veri dosyasının önizlemesini de görebilirsiniz:

![Veri kümesini içeri aktar iletişim kutusu](media/variable-explorer-import-dataset-dialog.png)
