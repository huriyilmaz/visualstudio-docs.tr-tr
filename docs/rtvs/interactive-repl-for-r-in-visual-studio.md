---
title: R için etkileşimli REPL
description: Visual Studio için, düzenleyici pencereleri ile tümleştirilmiş etkileşimli REPL ortamını kullanma.
ms.date: 06/28/2017
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: 0355f1017bb661b4f72325fb74f60653f69cd182
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878194"
---
# <a name="work-with-the-r-interactive-window"></a>R etkileşimli penceresiyle çalışma

Visual Studio için R Araçları (RTVS), bir **REPL** (Read-değerlendir-PRINT-Loop) penceresi olarak da bilinen, r kodunu girebileceğiniz ve sonuçları hemen görebileceğiniz r etkileşimli bir pencere sağlar. Tüm modüller, söz dizimi ve değişkenler, IntelliSense de etkileşimli pencerede kullanılabilir.

Etkileşimli pencere, normal R Düzenleyicisi pencereleri ile de tümleşiktir. Kod seçebilir ve CTRL tuşuna basabilir  + ya da sağ tıklayıp **etkileşimli olarak çalıştır**' ı seçerek kod, doğrudan yazmış gibi etkileşimli pencerede satır içine çalıştırılır. İmleç bir düzenleyici penceresinde tek satırundayken, **CTRL** + **ENTER** tuşu bu satırı etkileşimli pencereye gönderir ve ardından imleci bir sonraki satıra taşıdır. Bu şekilde, kodda ilerlemek için yalnızca **CTRL** + **tuşuna** tekrar tekrar basabilirsiniz.

Bu özelliklere ulaşmak için, bu makaledeki bölümleri ve [R ile çalışmaya başlama](getting-started-with-r.md) bölümünü izleyin. [Kod parçacıkları](code-snippets-for-r.md) , R Düzenleyicisi Windows 'da olduğu gibi etkileşimli pencerede da çalışır.

## <a name="overview-of-the-interactive-window"></a>Etkileşimli pencereye genel bakış

Satırın sonunda geçerli R kodu yazılması ve **ENTER** tuşuna basmak o satırdaki kodu çalıştırır:

```repl
> 3 + 3
[1] 6
```

Tek satırlı bir girişte her yere **ENTER** tuşuna basıldığında bu satır da çalıştırılır.

REPL içindeki tüm önceki giriş ve çıkış salt okunurdur ve değiştirilemez. Ancak, metni dilediğiniz zaman ve ayrıca yapıştırılan şekilde seçip kopyalayabilirsiniz. Yapıştırılan kod satır satıra göre girilmiş gibi çalışır.

Diğer bir deyişle, bir ifade yazmaya başladığınızda **ENTER** tuşuna bastığınızda rtvs, deyimin devam etmesi gerektiği zaman ve sol tarafta ve uygun girintide bulunan + istemiyle çok satırlı moda girer. RTVS, ayraçları, ayraçları ve süslü ayraçları da tamamlar:

![Etkileşimli penceredeki çok satırlı ekstre girişi](media/repl-multiline-entry.png)

Bu çok satırlı modda, **ENTER** tuşu yalnızca bloğun sonuna konumlandırıldığında kod bloğunu çalıştırır, aksi takdirde yeni bir satır ekler. Ancak,  + Bu kod bloğunu hemen çalıştırmak için herhangi bir konumda CTRL **ENTER** tuşuna basabilirsiniz.

### <a name="toolbar-commands"></a>Araç çubuğu komutları

Araç çubuğunun bulunduğu etkileşimli pencere aşağıda verilmiştir:

![Araç çubuğuyla etkileşimli pencere](media/repl-window.png)

Araç çubuğu komutları, çoğu, klavye eşdeğerleri olan ve **r** araçları  >  **oturumu** ve **r araçları**  >  **çalışma dizini** menülerinde (ya da belirtildiği gibi) kullanılabilen aşağıdaki gibidir:

| Düğme | Komut | Anahtar birleşimi | Description |
| --- | --- | --- | --- |
| ![Sıfırla düğmesi](media/repl-toolbar-01-reset.png) | Sıfırla | **CTRL** + **SHIFT** + **F10** | Etkileşimli pencere oturumunu sıfırlar ve tüm değişkenleri ve geçmişi temizleyerek. |
| ![Temizle düğmesi](media/repl-toolbar-02-clear.png) | Temizle | **CTRL** + **L** | Etkileşimli pencerede gösterilen çıktıyı temizler; oturum değişkenlerini veya geçmişi etkilemez. |
| ![Geçmiş düğmeleri](media/repl-toolbar-03-history.png) | Önceki geçmiş komutu<br/>Sonraki geçmiş komutu | **Yukarı**, **aşağı**<br/>**Alt** + **Yukarı**, **alt** + **aşağı** | Çok satırlı kod blokları için belirli davranışlar ile geçmişi kaydırır. Bkz. [Geçmiş](#history). |
| ![Çalışma alanını Yükle düğmesi](media/repl-toolbar-04-load-workspace.png) | Çalışma alanını yükle | yok | Önceki kaydedilmiş bir çalışma alanını yükler (bkz. [çalışma alanları ve oturumlar](#workspaces-and-sessions). |
| ![Çalışma alanını düğme olarak kaydet](media/repl-toolbar-05-save-workspace-as.png)| Çalışma alanını farklı kaydet | yok | Oturumun geçerli durumunu bir çalışma alanı olarak kaydeder (bkz. [çalışma alanları ve oturumlar](#workspaces-and-sessions). |
| ![Kaynak R betiği düğmesi](media/repl-toolbar-06-source-r-script.png) | Kaynak R betiği | **CTRL** + **SHIFT** + **S** | `source`Visual Studio düzenleyicisinde kodu çalıştıran Şu anda etkin olan R betiğine sahip çağrılar.  Bu düğme yalnızca Visual Studio düzenleyicisinde bir R dosyası açıksa görünür. |
| ![Yankı düğmesi ile kaynak R betiği](media/repl-toolbar-07-source-r-script-with-echo.png) | Echo ile kaynak R betiği | **CTRL** + **SHIFT** + Şunu **girin** | Kaynak R betiğiyle aynı ancak betiğin içeriğini etkileşimli pencerede görüntülüyor. |
| ![Kesme R düğmesi](media/repl-toolbar-08-interrupt-r.png)| Kesme R | **Esc** | Etkileşimli pencerede, `while` Bu bölümün başlangıcında ekran görüntüsündeki döngü gibi çalışan tüm kodu sonlandırır. |
| ![Hata ayıklayıcı Ekle düğmesi](media/repl-toolbar-09b-attach-debugger.png)| Hata ayıklayıcı Ekle | yok | Ayrıca,   >  **R etkileşim ekle** komutuyla hata ayıkla komutu kullanılarak da kullanılabilir. |
| ![Çalışma dizinini kaynak dosya konumu olarak ayarla düğmesi](media/repl-toolbar-10-set-working-directory-source.png)| Çalışma dizinini kaynak dosya konumuna ayarla | **CTRL** + **SHIFT** + **E** | Çalışma dizinini etkileşimli pencereye yüklenmiş en son kaynak dosya olarak ayarlar (kullanarak `source` ). Bkz. [çalışma dizini](#working-directory). |
| ![Çalışma dizinini proje konumuna ayarla düğmesi](media/repl-toolbar-11-set-working-directory-to-project.png) | Çalışma dizinini proje konumuna ayarla | **CTRL** + **SHIFT** + **P** | Çalışma dizinini, Visual Studio 'da Şu anda yüklü olan projenin köküne ayarlar. Bkz. [çalışma dizini](#working-directory). |
| (Metin alanı) | Çalışma dizini seçin | yok | Çalışma dizini için doğrudan giriş alanı. Bkz. [çalışma dizini](#working-directory). |

## <a name="workspaces-and-sessions"></a>Çalışma alanları ve oturumlar

Etkileşimli pencerede kod çalıştırmak, geçerli oturumunuzda bir bağlam oluşturur. Bağlam genel değişkenlerden, işlev tanımlarından, kitaplık yüklerine ve bu şekilde oluşur. Bu bağlam topluca bir *çalışma alanı* olarak adlandırılır ve istediğiniz zaman çalışma alanlarını kaydedebilir ve yükleyebilirsiniz.

**Çalışma alanını farklı kaydet** düğmesini veya **R araçları**  >  **oturumu** farklı  >  **Kaydet çalışma alanını** kullanarak bir konum ve dosya adı (varsayılan uzantı) istenir *. RData*).

Belirli bir dosya adı kullanarak bir çalışma alanını kaydetmek için (varsayılan değer *. RData*), REPL Içindeki **çalışma alanını Kaydet** düğmesine tıklayın:

Daha önce kaydedilen bir çalışma alanını yeniden yüklemek için **çalışma alanı yükle** düğmesini seçin veya **R araçları**  >  **oturum**  >  **yükleme çalışma alanını** kullanın ve çalışma alanı dosyasına gidin.

**Sıfırla** düğmesi veya **R araçları**  >  **oturum**  >  **sıfırlama** , oturum bağlamını temizler. Uzak bir oturum kullanıyorsanız, sıfırlama, uzak makinedeki kullanıcı profilini burada depolanan tüm dosyaları temizlemek için de siler. (Bkz. [çalışma alanları](r-workspaces-in-visual-studio.md#directories-on-local-and-remote-computers).)

## <a name="working-directory"></a>Çalışma dizini

Geliştiriciler, etkileşimli bir oturumda genellikle çalışma dizinini değiştirmek ister. Araç çubuğundaki, **R araçları**  >  **çalışma dizini** menüsündeki ve proje bağlam menüsündeki çeşitli komutlar, çalışma dizinini bir kaynak dosyasının, konumun veya projenizin veya başka herhangi bir rastgele konumun konumuna kolayca ayarlamanıza olanak sağlar. Bunun yapılması, dosyalara başvururken tam yol adları veya uzun göreli yol adları yazmalarını önlemenize yardımcı olur.

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