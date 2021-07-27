---
title: R Değişken Gezgini için Değişken Gezgini
description: Aşağıdaki Değişken Gezgini, Visual Studio R oturumunda belirli bir kapsamda yer alan tüm değişkenleri gösterir.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: da79f8e2fc40a0a64cc41d8571410c2a135a154a
ms.sourcegitcommit: fdba1b294b94e1f6a8e897810646873422393fff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2021
ms.locfileid: "114679738"
---
# <a name="variable-explorer"></a>Değişken Gezgini

**R** **Araçları Windows** Değişken Gezgini kullanılarak açılan Değişken Gezgini penceresi (veya R Araçları Veri Bilimi  >    >  **Ayarlar** kullandıysanız  + **Ctrl 8),**   >  geçerli R oturumunda belirli bir kapsamda yer alan tüm değişkenleri gösterir. Örneğin, Değişken Gezgini **penceresine** aşağıdaki satırları [girersiniz:](interactive-repl-for-r-in-visual-studio.md)

```R
x <- 42
y <- 43
n <- c(1,2,3,5,8,13)
```

Daha **Değişken Gezgini** penceresi aşağıdaki gibi görünür:

![Visual Studio'de değişken gezgini penceresi](media/variable-explorer-window.png)

Oturumda tanımlanmış daha karmaşık bir R veri çerçevenize sahipse verilere girebilirsiniz. Örneğin çalıştırdıktan `cars <- mtcars` sonra, veri kümesinde farklı düğümleri genişleterek veri kümesinde **gezinebilirsiniz Değişken Gezgini:**

![Görünümün genişletilmiş Değişken Gezgini](media/variable-explorer-expanded-results.png)

Değişkenleri silmek için, sağ tıklayın ve Sil'i **seçin** veya değişkeni seçin ve Sil **tuşuna** basın.

Artımlı arama kullanarak bir veri çerçevesinde gözlem de arayabilirsiniz. İlk olarak, aramak istediğiniz veri çerçevesindeki düğümleri genişletin ve arama kutusuna arama terimleri girin.

## <a name="details-table-view"></a>Ayrıntılar (tablo) görünümü

Veriler genellikle tablosal olduğundan, büyüteç simgesini seçerek veya sağ tıklar ve Ayrıntıları Göster'i seçerek herhangi bir karmaşık veri türünü ayrı bir tablo **olarak görüntüleyebilirsiniz.**

![Değişken Gezgini tablo görünümü](media/variable-explorer-table-view.png)

Bir sütun başlığına tıklar, verileri sütuna göre sıralar (artan ve azalan arasında değişiklik gösterir). Shift tuşunu **basılı** tutarak ek sütunlara tıklarsınız, bu sütunları da sıralamaya ekler. Shift olmadan bir **sütuna tıklar** ve tek sütunlu sıralamaya döner.

Sütun başlıklarına tıklama sıra, sıralamanın hangi sırayla gerçekleştirilecek olduğunu belirler. Örneğin **Shift** tuşunu basılı tutularak cyl sütununa ve ardından Shift tuşunu basılı tutularak mpg sütununa iki kez tıklarsanız, artan silindirler ve azalan mil/galon listesi +    +  sıralanmış olur: 

![İki sütuna göre veri sıralamanın tablo görünümü.](media/variable-explorer-table-view-sorting.png)

Tablo **Değişken Gezgini** ve tablo görünümleri ayrı ayrı Visual Studio, bunları yan yana çalışma için nasıl olduğu gibi ayarlayabilirsiniz. Genel [yönergeler için bkz. Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) pencere düzenlerini özelleştirme.

## <a name="open-in-excel-or-other-csv-capable-application"></a>Dosyalarda Excel (veya csv özellikli başka bir uygulama)

Daha fazla işleme ve analiz için oturum değişkenlerini CSV'ye dışarı aktarma genellikle yararlıdır. Dışarı aktarma, Değişken Gezgini'daki her düğümün yanındaki küçük Excel simgesiyle (Excel dışarı aktarma simgesi) veya bir öğeye sağ tıklar ve CSV Uygulamasında Aç'ı seçerek ![ ](media/variable-explorer-excel-icon.png) **yapılır.**  Simgeyi seçmek, *verileri %userprofile%\Documents\RTVS_CSV_Exports* klasöründeki yeni bir CSV dosyasına yazar ve ardından bu dosyayı başlatarak dosyayı.csvuzantısıyla ilişkili olan herhangi *bir uygulamada* açar.

## <a name="scopes"></a>Kapsamlar

Varsayılan olarak **Değişken Gezgini** genel kapsamda açılır. Pencerenin üst kısmında açılan listeden bir paket seçerek paket kapsamına geçebilirsiniz.

![Paket kapsamını gösteren değişken gezgini](media/variable-explorer-package-scopes.png)

Ayrıca hata ayıklayıcıda bir kesme noktası durdurulurken işlev kapsamına geçebilirsiniz (hata ayık Değişken Gezgini kodun işlev kapsamına otomatik olarak geçiş olmadığını unutmayın): 

![Değişken Gezgini sırasında veri çerçevesini gösteren veri çerçevesi](media/variable-explorer-as-locals-window.png)

**Değişken Gezgini,** bir işlevde yerel değişkenleri gösterme gibi hata ayıklayıcıda kod adım adım ilerlerken işlev kapsamını otomatik olarak değiştirir.

## <a name="import-data-into-variable-explorer"></a>Verileri Değişken Gezgini

R Araçları **Veri menüsünden de** kullanılabilen Değişken Gezgini araç çubuğundaki iki komut, **dış** CSV veri kümelerini R oturumunuz içine  >   aktarın: **Web URL'sinde** Veri Kümesi İçeri Aktar ve Metin Dosyasından Veri **Kümesi'ne R** Oturumuna Aktar.

İçeri aktaracak CSV dosyasını belirlediniz mi, Visual Studio  veri dosyasının nasıl ayrıştırıldıklarını (yani alan ayırıcısı nedir ve tırnakların nasıl işlensin) denetleme seçeneklerine sahip olduğunuz bir Veri Kümesi İçeri Aktar iletişim kutusunu görüntüler. Ayrıca, içe aktarılan veri çerçevesinin ve özgün veri dosyasının önizlemesini de görebilirsiniz:

![Veri kümesi içeri aktar iletişim kutusu](media/variable-explorer-import-dataset-dialog.png)
