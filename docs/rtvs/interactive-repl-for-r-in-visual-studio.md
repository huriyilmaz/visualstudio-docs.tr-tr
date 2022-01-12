---
title: R için etkileşimli REPL
description: Düzenleyici pencereleriyle tümleştirilmiş R inVisual Studio için etkileşimli REPL ortamını kullanma.
ms.date: 06/28/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: a942b59b06aebc079aaab220ff79be2868ed7974
ms.sourcegitcommit: dcecc0ed37b5e976b5dc83c5128ba5ecc8bc04b1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/04/2022
ms.locfileid: "135750570"
---
# <a name="work-with-the-r-interactive-window"></a>R etkileşimli penceresiyle çalışma

Visual Studio için R Araçları (RTVS), R kodu girip sonuçları hemen görmek için **REPL** (Read-Evaluate-Print-Loop) penceresi olarak da bilinen R etkileşimli bir pencere sağlar. IntelliSense'in yanı sıra tüm modüller, söz dizimi ve değişkenler etkileşimli pencerede kullanılabilir.

Etkileşimli pencere, normal R düzenleyicisi pencereleriyle de tümleştirilmiştir. Kodu seçerek **Ctrl** Enter tuşuna basabilir veya sağ tıklar ve Etkileşimli'de Yürüt'e tıklarsınız. Kod, etkileşimli pencerede doğrudan yazmış gibi satır satır + çalıştırıldı.  İmleç düzenleyici penceresindeki tek bir satırda **olduğunda, Ctrl** Enter bu satırı etkileşimli pencereye gönderir ve ardından imleci +  sonraki satıra taşır. Bu şekilde kodda adım adım **geçiş yapmak için Ctrl** + **Enter** tuşuna tekrar tekrar basabilirsiniz.

Bu özelliklerden deneyim için R [Kullanmaya başlayın](getting-started-with-r.md) yönergeleri ve bu makaledeki bölümleri izleyin. [Kod parçacıkları,](code-snippets-for-r.md) R düzenleyicisi pencerelerde olduğu gibi etkileşimli pencerede de çalışır.

## <a name="overview-of-the-interactive-window"></a>Etkileşimli Pencereye Genel Bakış

Geçerli R kodu yazmak ve **satırın** sonuna Enter tuşuna basmak kodu şu satırda çalıştırır:

```repl
> 3 + 3
[1] 6
```

Tek **satırlı** girişin herhangi bir yerinde Enter tuşuna bask o satırı da çalıştırır.

REPL'de önceki tüm giriş ve çıkışlar salt okunur olur ve değiştirilemez. Ancak istediğiniz zaman pencerede metinleri seçerek kopyalayıp yapıştırabilirsiniz. Yapıştıran kod satır satır girildi gibi çalışır.

Başka bir ifade yazmaya başladığınızda ve **Enter** tuşuna basladığınızda RTVS, deyimin ne zaman devam edeceğini bilir ve sol tarafta + istemi ve uygun girintiyi girerek çok satırlı moda girer. RTVS ayraçları, köşeli ayraçları ve küme ayraçlarını da tamamlar:

![Etkileşimli pencerede çok satırlı deyim girişi](media/repl-multiline-entry.png)

Bu çok satırlı **modda, Enter** anahtarı kod bloğu yalnızca bloğun sonuna konumlandırıldıklarında çalıştırır, aksi takdirde yeni bir satır ekler. Ancak, herhangi bir konumda **Ctrl** + **Enter** tuşuna basarak bu kod bloğuna hemen basabilirsiniz.

### <a name="toolbar-commands"></a>Araç çubuğu komutları

Araç çubuğundaki etkileşimli pencere şöyledir:

![Etkileşimli penceresi araç çubuğuyla görüntüleme](media/repl-window.png)

Araç çubuğu komutları aşağıdaki gibidir; bunların çoğu klavye eşdeğerlerine sahiptir ve R Araçları Oturumu ve **R Araçları** Çalışma Dizini menülerinde de kullanılabilir  >     >   (veya not edilen şekilde):

| Düğme | Komut | Tuş bileşimi | Description |
| --- | --- | --- | --- |
| ![Sıfırla düğmesi](media/repl-toolbar-01-reset.png) | Sıfırla | **Ctrl** + **Üstkrkt** + **F10** | Etkileşimli pencere oturumunu sıfırlar ve tüm değişkenleri ve geçmişi temizler. |
| ![Düğmeyi temizle](media/repl-toolbar-02-clear.png) | Temizle | **Ctrl** + **L** | Etkileşimli pencerede gösterilen çıkışı temizler; oturum değişkenlerini veya geçmişini etkilemez. |
| ![Geçmiş düğmeleri](media/repl-toolbar-03-history.png) | Önceki Geçmiş Komutu<br/>Sonraki Geçmiş Komutu | **Yukarı,** **Aşağı**<br/>**Alt** + **Yukarı,** **Alt** + **Aşağı** | Çok satırlı kod bloklarının belirli davranışlarıyla geçmişi kaydırarak. Bkz. [Geçmiş.](#history) |
| ![Çalışma alanını yükle düğmesi](media/repl-toolbar-04-load-workspace.png) | Çalışma Alanını Yükleme | yok | Daha önce kaydedilen bir çalışma alanını yükler (bkz. [Çalışma alanları ve oturumlar.](#workspaces-and-sessions) |
| ![Çalışma alanını farklı kaydet düğmesi](media/repl-toolbar-05-save-workspace-as.png)| Çalışma Alanını Farklı Kaydet | yok | Oturumun geçerli durumunu çalışma alanı olarak kaydeder (bkz. Çalışma [alanları ve oturumlar.](#workspaces-and-sessions) |
| ![Kaynak R betiği düğmesi](media/repl-toolbar-06-source-r-script.png) | Kaynak R Betiği | **Ctrl** + **Üstkrkt** + **S** | Şu `source` anda etkin olan R betiğiyle Visual Studio düzenleyicide kod çalıştıran çağrıları.  Bu düğme yalnızca bir R dosyası düzenleyicide açık Visual Studio görünür. |
| ![Yankı düğmesiyle kaynak R betiği](media/repl-toolbar-07-source-r-script-with-echo.png) | Echo ile Kaynak R Betiği | **Ctrl** + **Üstkrkt** + **Girin** | Kaynak R Betiği ile aynı ama betiğin içeriğini etkileşimli pencerede görüntüler. |
| ![R düğmesini kesme](media/repl-toolbar-08-interrupt-r.png)| R'yi kesintiye uğratma | **Esc** | Etkileşimli pencerede, bu bölümün başındaki ekran görüntüsünde yer alan döngü gibi çalışan `while` tüm kodu durdurur. |
| ![Hata ayıklayıcı ekle düğmesi](media/repl-toolbar-09b-attach-debugger.png)| Hata Ayıklayıcı ekleme | yok | Ayrıca Hata **Ayıklama'ya Ekle**  >  **komutu R Etkileşim** kullanılabilir. |
| ![Çalışma dizinini kaynak dosya konumu olarak ayarla düğmesi](media/repl-toolbar-10-set-working-directory-source.png)| Çalışma Dizini'nin Kaynak Dosya Konumu olarak ayarlayın | **Ctrl** + **Üstkrkt** + **E** | Çalışma dizinini etkileşimli pencereye yüklenen en son kaynak dosya olarak ayarlar `source` (kullanarak). Bkz. [Çalışma dizini.](#working-directory) |
| ![Çalışma dizinini proje konumu olarak ayarla düğmesi](media/repl-toolbar-11-set-working-directory-to-project.png) | Çalışma Dizini'Project Ayarlama | **Ctrl** + **Üstkrkt** + **P** | Çalışma dizinini, çalışma dizininde yüklü olan projenin kök dizinine Visual Studio. Bkz. [Çalışma dizini.](#working-directory) |
| (Metin alanı) | Çalışma Dizini'yi seçin | yok | Çalışma dizini için doğrudan giriş alanı. Bkz. [Çalışma dizini.](#working-directory) |

## <a name="workspaces-and-sessions"></a>Çalışma alanları ve oturumlar

Etkileşimli pencerede kod çalıştırma, geçerli oturumda bir bağlam oluşturmanızı sağlar. Bağlam genel değişkenler, işlev tanımları, kitaplık yükleri vb. içerir. Bu bağlam topluca çalışma alanı *olarak adlandırılan* ve çalışma alanlarını istediğiniz zaman kaydedebilirsiniz.

Çalışma Alanını Farklı **Kaydet düğmesini seçmek** veya R **Araçları** Oturum Çalışma Alanını Farklı Kaydet komutunu kullanmak bir konum ve dosya adı girmenizi ister  >    >   (varsayılan *uzantıdır). RData*).

Belirli bir dosya adını kullanarak çalışma alanını kaydetmek için (varsayılan *değerdir). RData*), **REPL'de** Çalışma Alanını Kaydet düğmesine tıklayın:

Daha önce kaydedilmiş bir çalışma alanını yeniden yüklemek için Çalışma **Alanını** Yükle düğmesini seçin veya **R Araçları** Oturum Yükleme Çalışma Alanını kullanın ve  >    >   çalışma alanı dosyasına gidin.

Sıfırla düğmesi **veya R Araçları**   >  **Oturum**  >  **Sıfırlaması** oturum bağlamını temizler. Uzak oturum kullanıyorsanız sıfırlama, uzak makinede depolanan tüm dosyaları temizlemek için kullanıcı profilini de siler. [(Bkz. Çalışma Alanları.)](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers)

## <a name="working-directory"></a>Çalışma dizini

Geliştiriciler genellikle etkileşimli bir oturumda çalışma dizinini değiştirmek ister. Araç çubuğunda, **R Araçları** Çalışma dizini menüsünde ve proje bağlam menüsünde bulunan çeşitli komutlar, çalışma dizinini bir kaynak dosyanın, konumun veya projenizin veya başka bir rastgele konumun konumunu kolayca ayarlamanızı  >   sağlar. Bunu yapmak, dosyalara başvuru yaparken tam yol adı veya uzun göreli yol adı yazmaktan kaçınmanıza yardımcı olur.

## <a name="history"></a>Geçmiş

Etkileşimli pencereye girdiğiniz her satıra, bir düzenleyiciden gönderilen satırlar dahil, REPL 'un geçmişinde korunur. Daha sonra, komut satırına alışkın olduğunuz gibi yukarı ve aşağı ok tuşlarıyla geçmiş üzerinden gezinebilirsiniz.

Tek fark, geçerli satırda yazmaya başladığınızda ve üzerine basarsanız, o satırı henüz çalıştırmadığınız takdirde bile geçerli satırın geçmişinizde korunduğu bir farklılık olur.

Etkileşimli penceredeki geçmiş Ayrıca, satırları kapsayan diğer kod bloğunun deyimleriyle sorunsuz bir şekilde çalışabilir. Yukarı ve aşağı ok tuşlarıyla geçmiş aracılığıyla geçiş yaparken, çok satırlı kod blokları bir bütün birim olarak alınır ve geçerli girdi olarak gösterilir. Bu noktada, ok tuşları, üst veya alt sınıra ulaşana kadar bu kod bloğu satırına satıra göre gider. Kod bloğunun en üstünde, yukarı ok geçmişteki bir önceki öğeyi alır; alt satırda aşağı ok bir sonraki öğeyi alır.

Bu davranış, geçmişteki son öğeyi bir yukarı ok ile yeniden çalıştırmak ve tuş vuruşu kombinasyonunu **girerken** , doğal olarak çok satırlı bir kod bloğunun düzenlenmesine Izin verirken yukarı oka basarak bir kez daha

Çok satırlı kod bloklarına gidilmemek için, araç çubuğu düğmelerini veya **alt** + ve **alt****alt tuşunu kullanın** - ve tüm bloklar tek bir satır olarak değerlendirilir.

Geçmiş özelliklerini çalıştırmanın en kolay yolu, bunları etkileşimli pencerede kendiniz denemaktır. Aşağıdaki kod, birkaç uygun tek ve çok satırlı deyimler sağlar. Her deyimle birlikte, uygun geçmişi oluşturmak için Kopyala seçeneğini kullanın. (Ayrıca, kodu ayrı bir kod dosyasına yapıştırabilirsiniz ve sonra **CTRL** + + ile çizgileri etkileşimli pencereye gönderebilirsiniz. **Girin**.)

```R
3 + 3

4 + 4

5 + 5

add <- function (x, y) {
  return (x + y)
}

sub <- function (x, y) {
  return (x - y)
}
```