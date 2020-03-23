---
title: Birlik için Görsel Stüdyo Araçlarına Genel Bakış | Microsoft Dokümanlar
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74298749"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçlarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, Visual Studio Tools for Unity'nin sunduğu özellikler ve Unity ile daha üretken olmak için bunları nasıl kullanabileceğiniz hakkında daha fazla bilgi edineceksiniz.  
  
 Visual Studio Tools for Unity *(VSTU)* ile Visual Studio'yu kullanarak C#'da oyun ve editör komut dosyaları yazabilir ve ardından hataları bulmak ve düzeltmek için güçlü hata ayıklama aracını kullanabilirsiniz. VSTU'nun en son sürümü, Unity'nin ShaderLab gölgeli dili, daha iyi hata ayıklayıcı görselleştirmeleri ve MonoBehavior sihirbazı için geliştirilmiş kod oluşturma için sözdizimi boyama içerir. VSTU ayrıca Unity proje dosyalarınızı, konsol mesajlarınızı ve oyununuzu Visual Studio'ya başlatabilme yeteneğinizi de getirir, böylece kod yazarken Unity Editor'a geçiş yapmak için daha az zaman harcayabilirsiniz.  
  
 Bu özellikler hakkında daha fazla bilgi edinmek için okumaya devam edin.  
  
## <a name="integration-with-unity"></a>Birlik ile Bütünleşme  
 Unity editörü ve Visual Studio arasında sürekli geçiş yapmak zorunda olsaydınız, Visual Studio Tools for Unity üretkenlik artırıcı olmazdı. Bu nedenle Visual Studio Tools for Unity, Visual Studio'dan ayrılmadan iş yapmayı kolaylaştırır.  
  
- **Unity Project Explorer,** Unity düzenleyicisinde görüntülenen hiyerarşiyi kullanarak görsel stüdyodaki tüm Birlik projenizi görüntüler.  
  
- Unity konsol entegrasyonu, Visual Studio'nun hata penceresinin hemen içinde Unity konsolundan çıktı görüntüler.  
  
- Visual Studio'dan oyununuzu hata ayıklamaya başlayın – Unity'ye geri dönmenize gerek yok, sadece F5 tuşuna basın.  
  
## <a name="superior-debugging"></a>Üstün Hata Ayıklama  
 İster tek başına ister Unity editöründe bağımsız olarak çalıştırılsın, C# komut dosyalarınızı ve DL'lerinizi hata ayıklamak için Visual Studio'nun güçlü hata ayıklayıcısını Unity oyununa bağlayın. Visual Studio'dan beklediğiniz tüm hata ayıklama özelliklerini kullanabilirsiniz.  
  
- Koşullu kesme noktaları da dahil olmak üzere kesme noktaları.  
  
- İzleme penceresindekarmaşık ifadeleri değerlendirin.  
  
- Değişkenlerin ve bağımsız değişkenlerin değerini inceleyin ve değiştirin.  
  
- Karmaşık nesnelere ve veri yapılarına ayrıntılı bilgi verin.  
  
  Ağınızdaki başka bir makinede çalışırken Unity oyununuzu bile hata ayıklayabilirsiniz.  
  
## <a name="productivity"></a>Üretkenlik  
 Visual Studio'nun C#'da kod yazma ve yeniden düzenleme için kurduğu üretkenliğe ek olarak, Visual Studio Tools for Unity geliştiricileri için ekstra üretkenlik özellikleri sağlar.  
  
- Unity'nin ShaderLab dili için sözdizimi boyama, gölgeli lerinizdeki hataları hata olmadan önce tespit etmenize yardımcı olur. ShaderLab dosyalarınızı Visual Studio'da açmanız.  
  
- MonoBehavior sihirbazı, Birlik davranışları listesine göz atmanıza olanak tanır ve aşina olmadığınız davranışlar için ortak kod oluşturur. CTRL+SHIFT+M tuşuna basın.  
  
- En çok kullandığınız Birlik davranışlarına aşina olduğunuzda, Hızlı MonoBehavior sihirbazı bunları parmaklarınızın ucuna getirir. CTRL+ALT+Q tuşuna basın.  
  
- Visual Studio'dan Unity belgelerine erişin. Öğrenmek istediğiniz API çağrısını vurgulayın, ardından CTRL+ALT+M, CTRL+H tuşlarına basın.  
  
- Klavye kısayolları ile tüm bu özelliklere ve daha fazlasına erişin.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Unity API için Visual Studio araçları  
 Sağlanan API'leri kullanarak Visual Studio Tools for Unity davranışını özelleştirin ve genişletin.  
  
- Visual Studio Tools for Unity, Unity konsoluna akış yapabilmesi için günlük geri arama kaydeder. Bilgileri kaydeden düzenleyici komut dosyalarınız varsa, iletilerinizi Visual Studio'ya göndermek için bunları aynı geri arama ya da bu komut dosyasına takabilirsiniz. Daha fazla bilgi için, Geri Arama Günlüğü örneğine bakın.  
  
- Unity stili geri arama ProjectFileGeneration'ı kullanarak Visual Studio Tools for Unity proje dosyalarını nasıl oluşturduğunu değiştirebilirsiniz. Daha fazla bilgi için Proje Dosyası Oluşturma örneğine bakın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Birlik Ana Sayfası](https://unity.com/)
