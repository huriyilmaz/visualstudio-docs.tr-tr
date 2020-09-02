---
title: "PTV 'leri kullanmaya başlama: kodu düzenleniyor | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 2e883970b4b265b1864d53ef6e1f347160e5aeb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550918"
---
# <a name="getting-started-with-ptvs-editing-code"></a>PTVS Kullanmaya Başlarken: Kodları Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTV 'ler, Python için üretken Visual Studio Düzenleyicisi deneyimi sağlar.  
  
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)izleyebilirsiniz.  
  
 Temel boş Python uygulaması proje şablonunu kullanmaya başlayın.  
  
 Düzenleyicide bir satır yazmaya başlayın `from … import` .  Açılır menü tamamlanma listesinin içeri aktarma için kullanılabilen modüllerin tam bir listesi olduğunu görürsünüz.  Bu liste, Python sürümünüze ve yüklediğiniz kitaplıklara göre farklılık gösterir.  Örnek olarak matematik kitaplığını kullanın.  Yazdığınız karakterler de dahil olmak üzere, bu öğelere yönelik tamamlama filtresi listesini yazdığınızda bu olduğunu fark edeceksiniz.  Tanımlayıcıyı içeri aktararak ifadeyi doldurun `sin` .  
  
```python  
from math import sin  
  
```  
  
 Kodlama sırasında, ilişkisiz olan ancak kitaplıklarınızda bulunan bir tanımlayıcı kullanırsanız, PTV 'ler, ihtiyacınız olan uygun içeri aktarma ekstresini eklemek için bir açılır hızlı çözüm sunar.  Örneğin, yazıp, `cos` **matematik 'dan içeri aktarma** seçeneğini görürsünüz.  
  
 Kod oluşturmak için bir kod parçacığı kullanabilirsiniz.  Düzenle menüsünde IntelliSense ' i seçin ve ardından kod parçacığı ekleyin.  Şimdi Python ve sonra def ' i seçin.  İşlevi çağırın `make_dot_string` ve bir parametre ekleyin `x` .  Sınama temelli geliştirme için şimdi dosyaya onaylar ekleyebilirsiniz ve PTV 'leri zaten tamamlanma listelerinde yeni işlevi sunabilir.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 Şimdi yeni işleve dönün ve aşağıdaki gövdeyi yazmaya başlayın:  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 PTV 'ler çağrı sitelerini bu işleve çözümleytiğinden PTV 'nin parametreyi bir tamsayı olduğunu varsaydığını görürsünüz.   İçeri aktarmak için hızlı düzelme de kullanmanız gerekecektir `radians` .  
  
 En üst düzeyde yazarak bir ana blok oluşturmak için başka bir kod parçacığı kullanın `main` , akıllı etiket Kullanıcı arabirimini çağırır ve "def Main...." seçeneğini belirlemek için Tab komutunu kullanın.  Çağırmak için bir temel döngü yazın `make_dot_string` .  Bkz. PTV 'ler işlevi, dönem ' e basabilir ve sunulan tamamlama ' yı görürseniz işlevin bir dize döndürdüğünü bilir.  Bu tür bilgileri tüm programınızın tamamında akacak, böylece değerlerinizin sonunda, kodunuzu daha iyi anlamanıza ve yazmanıza yardımcı olacak araç ipuçları ve tamamlamalar sağlayabiliriz.  
  
 Yazdırmak için bir çağrı ekleyin ve aşağıdakine benzer bir ana sahip olmanız gerekir:  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 F5 tuşuna basarsanız, kod cmd.exe pencerede çalışır ve ileri ve geri atma noktası olduğunu görürsünüz.  
  
 Bu yönergeleri, çok kısa bir [youtube videosunda](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)izleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Wiki belgeleri](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTV 'Leri kullanmaya başlama ve derinlemesine bakış videoları](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)
