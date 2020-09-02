---
title: "PTV 'leri kullanmaya başlama: hata ayıklama | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: b636dd4f3a5c5265231898573bfdf52de2dff84e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197706"
---
# <a name="getting-started-with-ptvs-debugging"></a>PTVS Kullanmaya Başlarken: Hata Ayıklama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio etkileşimli hata ayıklayıcı, Python kodunuzda sorunları tanılamayı ve çözmeyi kolaylaştırır.  
  
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4)izleyebilirsiniz.  
  
 Önceki Başlarken konusunda boş bir Python uygulaması projesi oluşturun ve PythonApplication1.py dosyasına aşağıdaki kodu girdiniz:  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 Genellikle Visual Studio 'da kod üzerinde çalışırken, F5 tuşuna basarak kodunuzu çalıştırmaya başlayabilirsiniz.  Bu komut, projenizin oluşturulması ve hata ayıklayıcı altında kodu çalıştırmaya başlaması gereken herhangi bir parçasını oluşturur.  Hata ayıklayıcı olmadan kodunuzu derlemek ve başlatmak için CTRL + F5 tuşlarına basabilirsiniz.  Hata ayıklayıcı ile kodunuz biraz daha yavaş çalışır, ancak bu maliyet için harika hata ayıklama özellikleri alırsınız.  
  
 Kodunuzu başlatmak için başka bir yol da, komut Içindeki adımla (normalde F11 'e bağlanır).  Bu, F5 gibidir, ancak her ifadede yürütmeyi duraklatır.  Programı belirli bir noktada bölmek istiyorsanız, bir kesme noktası ayarlamak için, kod düzenleyicisinin sol kenarındaki sol fare düğmesine basabilirsiniz.  F5 tuşuna bastığınızda programın yürütülmesi kesme noktasıyla birlikte kesilir veya durur.  Hata ayıklama menüsünün Adımlama için daha fazla seçeneği vardır; Örneğin, işlev çağrıları (F10) üzerinde adımla, işlev çağrılarına adımla (F11) veya bir işlevin sonuna atlayın (Shift-F11).  
  
 Hata ayıklayıcıda kesildiğinde yapabileceğiniz daha fazla bilgi vardır.  Yereller penceresi yerel değişkenlerin geçerli değerlerini gösterir.  Kodunuzun adımında, Yereller otomatik olarak güncelleştirmeleri görüntüler.  Yürütmenin durdurulduğu geçerli satıra yakın değişkenleri gösteren oto penceresi.  İzleme penceresi, her yürütme durdurulduğunda hata ayıklayıcının otomatik olarak güncelleşmesi için herhangi bir Python ifadesi yazabilirsiniz.  Ayrıca, değişkenin değerlerinin bir açılır görünümünü görmek için işaretçiyi düzenleyici penceresinde değişkenlerin üzerine getirebilirsiniz. bu veri ipucu ekranı, nesneleri incelemenize olanak sağlar.  Bazı veri türleri, veri ipucu görüntüsünü (örneğin, HTML, XML veya JSON gibi özel biçimlendirmeye sahip dizeler) erişilebilen özel Görselleştiriciler vardır.  
  
 Çağrı yığını penceresi, hata ayıklayıcının durdurulduğu geçerli ifadeye işaret eden bekleyen işlev çağrılarını gösterir.  Her işlevde kodun yürütmeye devam edebilecekleri yere gitmek için farklı yığın çerçeveleri (çağrı yığınında satırlar) seçebilirsiniz.  
  
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4)izleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTV 'Leri kullanmaya başlama ve derinlemesine bakış videoları](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
