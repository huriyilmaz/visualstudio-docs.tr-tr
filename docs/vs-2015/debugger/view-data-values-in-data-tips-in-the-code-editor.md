---
title: Kod düzenleyicisinde veri Ipuçlarında veri değerlerini görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], DataTips
- DataTips tool
ms.assetid: ffa7bd18-439b-4685-a9b3-c7884b5de41f
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fd2c7bf67b5c2e7f25b4193462883b53cda8db87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700104"
---
# <a name="view-data-values-in-data-tips--in-the-code-editor"></a>Veri İpuçları'ndaki veri değerlerini kod düzenleyicide görüntüleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataTips, hata ayıklama sırasında programınızdaki değişkenlerle ilgili bilgileri görüntülemek için kullanışlı bir yol sağlar. DataTips yalnızca kesme modunda ve yalnızca geçerli yürütme kapsamındaki değişkenlerle çalışır.  
  
 ' De [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] , veri ipuçları kaynak dosyadaki belirli bir konuma sabitlenebilir veya tüm pencerelerin üzerine taşınabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-display-a-datatip-in-break-mode-only"></a>Bir Datatıp 'yi göstermek için (yalnızca kesme modunda)  
  
1. Bir kaynak penceresinde, fare işaretçisini geçerli kapsamdaki herhangi bir değişken üzerine getirin.  
  
    Bir veri Ipucu görünür.  
  
   > [!NOTE]
   > Veri ipuçları her zaman yürütmenin askıya alındığı ve imlecin nerede olduğu bağlamında değerlendirilir. Geçerli bağlamdaki bir değişkenle aynı ada sahip başka bir işlevde bulunan bir değişkenin üzerine geldiğinizde, diğer işlevdeki değişkenin değeri geçerli bağlamda değişkenin değeri olarak görüntülenir.  
  
2. Fare işaretçisini kaldırdığınızda veri Ipucu kaybolur. Veri Ipucunu açık kalacak şekilde sabitlemek için, **kaynağa sabitle** simgesine tıklayın veya  
  
   - Bir değişkene sağ tıklayıp **kaynağa sabitle**' ye tıklayın.  
  
     Sabitlenen veri Ipucu hata ayıklama oturumu sona erdiğinde kapanır.  
  
### <a name="to-unpin-a-datatip-and-make-it-float"></a>Bir Datatıp 'yi çıkarmak ve kayan hale getirmek için  
  
- Sabitlenmiş bir veri Ipucunda **kaynaktan ayır** simgesine tıklayın.  
  
     PIN simgesi sabitlenmemiş konuma dönüşür. Datatıp artık açık pencerelerin üzerine kayarak eklenmiştir. Kayan veri Ipucu hata ayıklama oturumu sona erdiğinde kapanır.  
  
### <a name="to-repin-a-floating-datatip"></a>Kayan veri Ipucunda  
  
- Bir veri Ipucunda sabitleme simgesine tıklayın.  
  
     PIN simgesi sabitlenmiş konuma değişir. DataTip bir kaynak penceresinin dışındaysa, PIN simgesi devre dışıdır ve Datatıp sabitlenemez.  
  
### <a name="to-close-a-datatip"></a>Bir veri Ipucunu kapatmak için  
  
- Fare işaretçisini bir DataTip üzerine getirin ve ardından **Kapat** simgesine tıklayın.  
  
### <a name="to-close-all-datatips"></a>Tüm veri Ipuçlarını kapatmak için  
  
- **Hata Ayıkla** menüsünde **tüm veri ipuçlarını temizle**' ye tıklayın.  
  
### <a name="to-close-all-datatips-for-a-specific-file"></a>Belirli bir dosyanın tüm veri Ipuçlarını kapatmak için  
  
- **Hata Ayıkla** menüsünde, *dosyaya* **sabitlenmiş tüm veri ipuçlarını temizle** ' ye tıklayın.  
  
## <a name="expanding-and-editing-information"></a>Bilgiler genişletiliyor ve düzenleniyor  
 Üyelerini görüntülemek için bir diziyi, yapıyı veya nesneyi genişletmek üzere DataTips kullanabilirsiniz. Bir değişkenin değerini bir veri Ipucundan de düzenleyebilirsiniz.  
  
#### <a name="to-expand-a-variable-to-see-its-elements"></a>Öğelerini görmek için bir değişkeni genişletmek için  
  
- Bir veri Ipucunda, fare işaretçisini **+** değişken adından önce gelen işaretin üzerine getirin.  
  
     Değişkeni, öğelerini ağaç biçiminde göstermek için genişler.  
  
     Değişken genişletildiğinde, klavyenizdeki ok tuşlarını kullanarak yukarı ve aşağı hareket edebilirsiniz. Alternatif olarak, fareyi de kullanabilirsiniz.  
  
#### <a name="to-edit-the-value-of-a-variable-using-a-datatip"></a>DataTip kullanarak bir değişkenin değerini düzenlemek için  
  
1. Bir veri Ipucunda, değere tıklayın. Bu salt okuma değerleri için devre dışıdır.  
  
2. Yeni bir değer yazın ve ENTER tuşuna basın.  
  
## <a name="making-a-datatip-transparent"></a>DataTip saydam yapma  
 Bir veri Ipucunun arkasındaki kodu görmek isterseniz, veri Ipucunu geçici olarak saydam hale getirebilirsiniz. Bu, sabitlenmiş veya kayan veri Ipuçları için geçerlidir.  
  
#### <a name="to-make-a-datatip-transparent"></a>Bir veri Ipucunu saydam hale getirmek için  
  
- Bir veri Ipucunda, CTRL tuşuna basın.  
  
     CTRL tuşunu basılı tuttuğunuz sürece Datatıp saydam kalır.  
  
## <a name="visualizing-complex-data-types"></a>Karmaşık veri türlerini görselleştirme  
 Veri Ipucunda bir değişken adının yanında bir büyüteç simgesi görünürse, bu veri türü değişkenleri için bir veya daha fazla [özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md) vardır. Bilgileri daha anlamlı, genellikle grafik gibi bir şekilde göstermek için Görselleştirici kullanabilirsiniz.  
  
#### <a name="to-view-the-contents-of-a-variable-using-a-visualizer"></a>Görselleştirici kullanarak bir değişkenin içeriğini görüntülemek için  
  
- Veri türü için varsayılan Görselleştiriciyi seçmek üzere büyüteç simgesine tıklayın.  
  
     -veya-  
  
     Görselin yanındaki açılır oka tıklayarak veri türü için uygun Görselleştiriciler listesinden seçim yapın.  
  
     Görselleştirici, bilgileri görüntüler.  
  
## <a name="adding-information-to-a-watch-window"></a>Izleme penceresine bilgi ekleme  
 Bir değişkeni izlemeye devam etmek istiyorsanız, bir veri Ipucundan **Gözcü** penceresine değişkeni ekleyebilirsiniz.  
  
#### <a name="to-add-a-variable-to-the-watch-window"></a>izleme penceresi bir değişken eklemek için  
  
- Bir Datatıp öğesine sağ tıklayın ve ardından **Gözcü Ekle**' ye tıklayın.  
  
     Değişken, **Gözcü** penceresine eklenir. Birden çok **Gözcü** pencerelerini destekleyen bir sürüm kullanıyorsanız, değişken **1. gözcü** 'e eklenir.  
  
## <a name="importing-and-exporting-datatips"></a>Veri Ipuçlarını içeri ve dışarı aktarma  
 Bir iş arkadaşınızla paylaşılabilen veya metin Düzenleyicisi kullanılarak düzenlenebilen bir XML dosyasına DataTips aktarabilirsiniz.  
  
#### <a name="to-export-datatips"></a>Veri Ipuçlarını dışarı aktarmak için  
  
1. Hata Ayıkla menüsünde, **veri Ipuçlarını dışarı aktar**' a tıklayın.  
  
     **Veri Ipuçlarını dışarı aktar** iletişim kutusu görünür.  
  
2. Standart dosya tekniklerini kullanarak XML dosyasını kaydetmek istediğiniz konuma gidin, dosya **adı** kutusuna dosya için bir ad yazın ve ardından **Tamam**' a tıklayın.  
  
#### <a name="to-import-datatips"></a>Veri Ipuçlarını Içeri aktarmak için  
  
1. Hata Ayıkla menüsünde, **veri Ipuçlarını Içeri aktar**' a tıklayın.  
  
     **Veri Ipuçlarını Içeri aktar** iletişim kutusu görünür.  
  
2. Açmak istediğiniz XML dosyasını bulmak için iletişim kutusunu kullanın ve **Tamam**' a tıklayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata ayıklayıcıda verileri görüntüleme](../debugger/viewing-data-in-the-debugger.md)   
 [Nasıl yapılır: QuickWatch Iletişim kutusunu kullanma](https://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Özel Görselleştiriciler oluşturma](../debugger/create-custom-visualizers-of-data.md)   
 [Nasıl yapılır: hata ayıklayıcı pencerelerinin sayısal biçimini değiştirme](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)
