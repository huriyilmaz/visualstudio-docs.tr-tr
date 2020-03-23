---
title: R için Etkileşimli REPL
description: Editör pencereleri ile entegre r inVisual Studio için etkileşimli REPL ortamı nasıl kullanılır.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 7109e74e858aa308b8f49e6e1e335478f801070b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62815000"
---
# <a name="work-with-the-r-interactive-window"></a>R etkileşimli penceresi ile çalışma

R Tools for Visual Studio (RTVS), **Repl** (Oku-Değerlendir-Yazdır-Döngü) penceresi olarak da bilinen ve R kodunu girebileceğiniz ve sonuçları hemen görebileceğiniz bir R etkileşimli pencere sağlar. Tüm modüller, sözdizimi ve değişkenlerin yanı sıra IntelliSense etkileşimli pencerede kullanılabilir.

Etkileşimli pencere aynı zamanda normal R düzenleyici pencereleri ile entegre edilmiştir. Kodu seçebilir ve **Ctrl**+**Enter**tuşuna basabilir veya **Etkileşimli'de Yürüt'e**sağ tıklayıp Yürüt'ün'u seçebilir ve kod, doğrudan yazargibi etkileşimli pencerede satır satır çalıştırılır. İmleç düzenleyici penceresinde tek bir satırda yken, **Ctrl**+**Enter** bu satırı etkileşimli pencereye gönderir ve imleci bir sonraki satıra taşır. Bu şekilde, kodu aşmak için **Ctrl**+**Enter** tuşuna tekrar tekrar basmanız nıza yardımcı olabilir.

Bu özellikleri deneyimlemek için, Bu makaledeki bölümlerin yanı sıra R walkthrough [ile başlayın'ı](getting-started-with-r.md) izleyin. [Kod parçacıkları,](code-snippets-for-r.md) R düzenleyici pencerelerinde olduğu gibi etkileşimli pencerede de çalışır.

## <a name="overview-of-the-interactive-window"></a>Etkileşimli Pencereye Genel Bakış

Geçerli R kodu yazmak ve satırın sonunda **Enter** tuşuna basmak kodu bu satırda çalıştırır:

```repl
> 3 + 3
[1] 6
```

Tek satırlı girişte herhangi bir yerde **Enter** tuşuna bastığınızda bu satırı da çalıştırın.

REPL'deki tüm önceki giriş ve çıktılar salt okunur ve değiştirilemez. Ancak, istediğiniz zaman pencereden metin seçebilir ve kopyalayabilir ve yapıştırAbilirsiniz. Yapıştırılan kod satır satır girilmiş gibi çalışır.

Yani, bir ifade yazmaya başladığınızda ve **Enter**tuşuna bastığınızda, RTVS deyimi devam edilmesi gereken zaman bilir ve sol ve uygun girintinlik bir + komut istemi ile çok satırlı modugirer. RTVS ayrıca parantezleri, parantezleri ve kıvırcık ayraçları da tamamlar:

![Etkileşimli pencerede çok satırlı ekstre girişi](media/repl-multiline-entry.png)

Bu çok satırlı modda, **Enter** tuşu kod bloğunu yalnızca bloğun sonuna yerleştirildiğinde çalıştırır, aksi takdirde yeni bir satır ekler. Ancak, bu kod bloğunu hemen çalıştırmak için herhangi bir konumda **Ctrl**+**Enter** tuşuna basabilirsiniz.

### <a name="toolbar-commands"></a>Araç çubuğu komutları

Araç çubuğuna sahip etkileşimli pencere aşağıda veda edebilirsiniz:

![Araç çubuğu ile etkileşimli pencere](media/repl-window.png)

Araç çubuğu komutları aşağıdaki gibidir, bunların çoğu klavye eşdeğerleri vardır ve **R Tools** > **Session** ve **R Tools** > **Working Directory** menülerinde (veya belirtildiği gibi) da mevcuttur:

| Düğme | Komut | Anahtar kombinasyonu | Açıklama |
| --- | --- | --- | --- |
| ![Sıfırlama düğmesi](media/repl-toolbar-01-reset.png) | Sıfırla | **Ctrl**+**Shift**+**F10** | Etkileşimli pencere oturumunu sıfırlar, tüm değişkenleri ve geçmişi temizler. |
| ![Düğmeyi temizle](media/repl-toolbar-02-clear.png) | Temizle | **Ctrl**+**L** | Etkileşimli pencerede gösterilen çıktıyı temizler; oturum değişkenlerini veya geçmişini etkilemez. |
| ![Geçmiş düğmeleri](media/repl-toolbar-03-history.png) | Önceki Geçmiş Komutu<br/>Sonraki Geçmiş Komutu | **Yukarı**, **Aşağı**<br/>**Alt**+**Yukarı**, **Alt**+**Aşağı** | Çok satırlı kod blokları için belirli davranışlarla birlikte geçmiş boyunca kaydırılır. [Bkz. Tarih](#history). |
| ![Çalışma alanı düğmesini yükleyin](media/repl-toolbar-04-load-workspace.png) | Yük Çalışma Alanı | yok | Önceki kaydedilmiş çalışma alanını yükler (bkz. [Çalışma Alanları ve oturumlar.](#workspaces-and-sessions) |
| ![Çalışma alanını düğme olarak kaydedin](media/repl-toolbar-05-save-workspace-as.png)| Çalışma Alanını Olduğu Gibi Kaydet | yok | Oturumun geçerli durumunu çalışma alanı olarak kaydeder (bkz. [Çalışma Alanları ve oturumlar.](#workspaces-and-sessions) |
| ![Kaynak R komut dosyası düğmesi](media/repl-toolbar-06-source-r-script.png) | Kaynak R Script | **Ctrl**+**Vites**+**S** | Kodu `source` çalıştıran Visual Studio düzenleyicisinde şu anda etkin olan R komut dosyasıyla arama lar.  Bu düğme yalnızca Visual Studio düzenleyicisinde bir R dosyası açıldığında görüntülenir. |
| ![Yankı düğmesi ile Kaynak R komut dosyası](media/repl-toolbar-07-source-r-script-with-echo.png) | Echo ile Kaynak R Script | **Ctrl**+**Shift**+**Girin** | Source R Script ile aynı ancak komut dosyasının içeriğini etkileşimli pencerede görüntüler. |
| ![Kesme R düğmesi](media/repl-toolbar-08-interrupt-r.png)| Kesme R | **Esc** | Bu bölümün başında ekran görüntüsündeki `while` döngü gibi etkileşimli penceredeki tüm çalışan kodları durdurur. |
| ![Hata ayıklama düğmesini ekleme](media/repl-toolbar-09b-attach-debugger.png)| Hata Ayıklama tak | yok | Ayrıca Hata **Ayıklama** > **R Interactive** komutunu kullanarak kullanılabilir. |
| ![Çalışma dizini kaynak dosya konumu düğmesine ayarlama](media/repl-toolbar-10-set-working-directory-source.png)| Çalışma Dizini Kaynak Dosya Konumuna Ayarlama | **Ctrl**+**Vites**+**E** | Çalışma dizini, etkileşimli pencereye yüklenen (kullanarak) `source`en son kaynaklı dosyaya ayarlar. Bkz. [Çalışma dizini.](#working-directory) |
| ![Çalışma dizini proje konumu düğmesine ayarlama](media/repl-toolbar-11-set-working-directory-to-project.png) | Çalışma Dizini Proje Konumuna Ayarlayın | **Ctrl**+**Shift**+**P** | Çalışma dizini Visual Studio'da şu anda yüklenen projenin köküne ayarlar. Bkz. [Çalışma dizini.](#working-directory) |
| (Metin alanı) | Çalışma Dizini Seçin | yok | Çalışma dizini için doğrudan giriş alanı. Bkz. [Çalışma dizini.](#working-directory) |

## <a name="workspaces-and-sessions"></a>Çalışma alanları ve oturumlar

Etkileşimli pencerede kod çalıştırmak, geçerli oturumunuzda bir bağlam oluşturur. Bağlam, genel değişkenler, işlev tanımları, kitaplık yükleri vb. oluşur. Bu bağlam topluca *çalışma alanı*olarak adlandırılır ve istediğiniz zaman çalışma alanlarını kaydedebilir ve yükleyebilirsiniz.

**Çalışma Alanını Kaydet** düğmesini seçmek veya **R Tools** > **Session'ı** > kullanarak**Çalışma Alanını Kaydet** komutu olarak bir konum ve dosya adı için sizi ister (varsayılan uzantı. * RData*).

Belirli bir dosya adı kullanarak çalışma alanını kaydetmek için (varsayılan *değer. RData*), REPL'deki **Çalışma Alanını Kaydet** düğmesine tıklayın:

Önceden kaydedilmiş bir çalışma alanını yeniden yüklemek **için, Çalışma Alanını Yükle** düğmesini seçin veya **R Tools** > **Session** > **Load Workspace'i** kullanın ve çalışma alanı dosyasına gidin.

**Sıfırlama** düğmesi veya **R Araçları** > **Oturumu** > **Sıfırlama** oturumu bağlamını temizler. Uzaktan bir oturum kullanıyorsanız, sıfırlama, uzaktaki makinedeki kullanıcı profilini de siler ve orada depolanan tüm dosyaları temizler. (Bkz. [Çalışma Alanları](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Çalışma dizini

Geliştiriciler genellikle etkileşimli bir oturumda çalışırken çalışma dizini değiştirmek istiyorum. Araç çubuğunda, **R Araçları** > **Çalışma dizini** menüsünde ve proje bağlamı menüsünde bulunan çeşitli komutlar, çalışma diziniyle kaynak dosyanın konumuna, konuma veya projenize veya başka bir rasgele konuma kolayca ayarlayasınız. Bunu yapmak, dosyalara atıfta bulunurken tam yol adlarını veya uzun göreli yol adlarını yazmaktan kaçınmanıza yardımcı olur.

## <a name="history"></a>Geçmiş

Etkileşimli pencereye girdiğiniz her satır, bir düzenleyiciden gönderilen satırları içerir, REPL'nin geçmişinde korunur. Daha sonra, komut satırında alışık olduğunuz gibi Yukarı ve Aşağı ok tuşları ile tarih boyunca gezinebilirsiniz.

Bir fark, geçerli satırda yazmaya başlar ve Yukarı tuşuna basatırsanız, bu satır, henüz bu satırı çalıştırmamış olsanız bile, geçerli satır ın geçmişinizde korunmuş olmasıdır.

Etkileşimli penceredeki geçmiş, satırları kapsayan diğer kod bloğu ifadeleri ile de akıllıca çalışır. Yukarı ve Aşağı ok tuşları ile tarih boyunca bisiklet sürerken, çok satırlı kod blokları bir bütün birim olarak alınır ve geçerli giriş olarak gösterilir. Bu noktada, ok tuşları üst veya alt ulaşılana kadar, bu kod blok satırı satır gezinmek. Kod bloğunun üst kısmında, yukarı ok geçmişteki önceki öğeyi alır; alt satırda, aşağı ok sonraki öğeyi alır.

Bu davranış, bir Yukarı ok ve **Enter** tuş vuruşu birleşimi ile tarihteki son öğeyi yeniden çalıştırma tipik bir durumda barındırır, doğal olarak içine gezinmek için Yukarı ok tuşuna basarak çok satırlı kod bloğu düzenleme için izin verir.

Çok satırlı kod bloklarında gezinmeyi önlemek için araç çubuğu düğmelerini veya **Alt**+**Up** and **Alt**-**Down**düğmelerini kullanın ve bu blokların tümü tek bir satır olarak kabul edilir.

Geçmiş özelliklerini deneyimlemenin en kolay yolu, bunları etkileşimli pencerede kendiniz denemektir. Aşağıdaki kod birkaç uygun tek ve çok satırlı ifadeler sağlar. Ancak, uygun geçmişi oluşturmak için her ifadeyle birlikte kopyala-yapıştır'ı ayrı ayrı kullanın. (Ayrıca kodu ayrı bir kod dosyasına yapıştırıp **ctrl**+**enter**ile satırları etkileşimli pencereye gönderebilirsiniz.)

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