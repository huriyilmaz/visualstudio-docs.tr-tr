---
title: R için Değişken Gezgin
description: Visual Studio'daki Değişken Gezgin, geçerli R oturumunda belirli bir kapsamdaki tüm değişkenleri gösterir.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 799b7f2789898e0d02d9588f9a3ad7d1e8098a00
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62809877"
---
# <a name="variable-explorer"></a>Değişken Gezgini

**R Tools** > **Windows** > Variable**Explorer** (veya **R Tools** > **Veri Bilimi Ayarlarını**kullandıysanız **Ctrl**+**8)** kullanılarak açılan **Değişken Gezgin** penceresi, geçerli R oturumunda belirli bir kapsamdaki tüm değişkenleri gösterir. Örneğin, **Değişken Gezgini'ni** açıp [etkileşimli pencereye](interactive-repl-for-r-in-visual-studio.md)aşağıdaki satırları girerseniz:

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

**Değişken Gezgin** penceresi sonra aşağıdaki gibi görünür:

![Visual Studio'da değişken explorer penceresi](media/variable-explorer-window.png)

Oturumda tanımlanan daha karmaşık bir R veri çerçeveniz varsa, verilere yönlendirebilirsiniz. Örneğin, çalıştırdıktan `cars <- mtcars` sonra Değişken Gezgini'ndeki farklı düğümleri genişleterek **Variable Explorer**veri kümesinde gezinebilirsiniz:

![Değişken Gezginin genişletilmiş görünümü](media/variable-explorer-expanded-results.png)

Değişkenleri silmek için Sağ tıklatın ve **Sil'i**seçin veya değişkeni seçin ve **Sil** tuşuna basın.

Artımlı aramayı kullanarak veri çerçevesinde bir gözlem de arayabilirsiniz. Önce, aramak istediğiniz veri çerçevesindeki düğümleri genişletin, ardından arama kutusuna arama terimleri girin.

## <a name="details-table-view"></a>Ayrıntılar (tablo) görünümü

Veriler genellikle aynı olduğundan, büyüteç simgesini seçerek veya ayrıntıları **göster'i**seçerek herhangi bir karmaşık veri türünü ayrı bir tablo olarak görüntüleyebilirsiniz.

![Değişken Gezgin tablo görünümü](media/variable-explorer-table-view.png)

Bir sütun başlığına tıkladığınızda verileri sütuna göre sıralar (artan ve azalan arasında dönüşümlü). **Shift'i** basılı tutmak ve ek sütunları tıklatmak bu sütunları sıralamaya da ekler. **Shift** olmayan bir sütunu tıklatmak tek sütun sıralamasına döner.

Sütun başlıklarını tıklatma sırası, sıralamanın gerçekleştirilme sırasını belirler. Örneğin, **Shift**+ **cyl** sütununa**tıklayın,** sonra **Shift**+artan silindirler ve azalan mil başına galon için listeyi sıralamak için iki kez **mpg** sütununa**tıklayın:**

![İki sütuna göre veri sıralama tablo görünümü.](media/variable-explorer-table-view-sorting.png)

**Değişken Gezginve** tablo görünümleri ayrı Visual Studio pencerelerinde olduğundan, bunları yan yana çalışma için istediğiniz gibi düzenleyebilirsiniz. Genel yönergeler için [Visual Studio'daki pencere düzenlerini özelleştir'e](../ide/customizing-window-layouts-in-visual-studio.md) bakın.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Excel'de açık (veya diğer CSV özellikli uygulama)

Daha fazla manipülasyon ve analiz için, oturum değişkenlerini CSV'ye aktarmak genellikle yararlıdır. Dışa aktarma, **Değişken Gezgini'ndeki**](media/variable-explorer-excel-icon.png)her düğümün yanındaki küçük Excel simgesi (Excel![dışaak simgesi) ile veya bir öğeyi sağ tıklatarak ve **CSV Uygulamasında Aç'ı**seçerek yapılır. Simgeyi seçmek, verileri *%userprofile%\Documents\RTVS_CSV_Exports* klasöründe yeni bir CSV dosyasına yazar ve ardından *.csv* uzantısı ile ilişkili olan uygulamada açan bu dosyayı başlatır.

## <a name="scopes"></a>Kapsamlar

Varsayılan olarak **Değişken Gezgini** genel kapsama açılır. Pencerenin üst kısmındaki açılır pencereden bir paket seçerek paket kapsamına geçebilirsiniz.

![Paket kapsamını gösteren değişken gezgin](media/variable-explorer-package-scopes.png)

Hata ayıklayıcıdaki bir kesme noktasında durdurulduğunda işlev kapsamına da geçebilirsiniz **(Değişken Gezginin** hata ayıklanan kodun işlev kapsamına otomatik olarak geçmediğini unutmayın):

![Hata ayıklama sırasında bir veri çerçevesi gösteren Değişken Gezgin](media/variable-explorer-as-locals-window.png)

**Değişken Gezgin,** hata ayıklayıcıda yerel değişkenleri bir işlevde göstermek gibi koda adım attıkça işlev kapsamını otomatik olarak değiştirir.

## <a name="import-data-into-variable-explorer"></a>Verileri Değişken Gezgine aktarma

**R Araçları** > **Veri** menüsünden de kullanılabilen Değişken **Gezgin** araç çubuğundaki iki komut, R oturumunuza harici CSV veri kümelerini içe aktarın: Veri **kümesini Web URL'sinden R Oturumuna aktarın** ve **Text File'dan R Session'a Veri Kümesi'ni aktarın.**

İçe aktarılacağı CSV dosyasını tanımladıktan sonra Visual Studio, veri dosyasının nasıl ayrıştırılacağını (diğer bir deyişle alan ayırıcısının ne olduğunu ve tırnak ların nasıl işleyeceğini) denetleme seçenekleriniz olan bir **Alma Veri Kümesi** iletişim kutusu görüntüler. Ayrıca, içe aktarılan veri çerçevesinin ve özgün veri dosyasının önizlemesini de görebilirsiniz:

![Veri kümesi iletişim kutusunu içe aktarma](media/variable-explorer-import-dataset-dialog.png)
