---
title: Unity için Visual Studio Araçları genel bakış | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: overview
ms.assetid: b4231bb9-45c4-4c77-ac3c-d05033b26393
caps.latest.revision: 6
ms.author: crdun
manager: crdun
ms.openlocfilehash: ba5447301c3a5581d35825ed91c17b3c9f50015f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298749"
---
# <a name="overview-of-visual-studio-tools-for-unity"></a>Unity için Visual Studio Araçlarına Genel Bakış
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu bölümde, Özellikler Unity için Visual Studio Araçları teklifler ve Unity ile daha üretken olmak için bunları nasıl kullanabileceğiniz hakkında daha fazla bilgi edineceksiniz.  
  
 Unity için Visual Studio Araçları (*VSTU*) Ile Visual Studio 'yu kullanarak içindeki C# oyun ve düzenleyici betikleri yazabilir ve ardından hataları bulmak ve onarmak için güçlü hata ayıklayıcıyı kullanabilirsiniz. VSTU 'nın en son sürümü, Unity 'nin ShaderLab gölgelendirici dili, daha iyi hata ayıklayıcı görselleştirmeleri ve MonoBehavior Sihirbazı için geliştirilmiş kod oluşturma için Sözdizimi renklendirmesi içerir. VSTU, Unity proje dosyalarınızı, konsol iletileri ve daha az zaman için ve Unity Düzenleyicisi'nden kod yazarken geçiş ayırmasına oyununuzu Visual Studio'ya başlatma özelliğini de getirir.  
  
 Bu özellikler hakkında daha fazla bilgi edinmek için okumaya devam edin.  
  
## <a name="integration-with-unity"></a>Unity ile tümleştirme  
 Unity Düzenleyicisi ve Visual Studio ile her zaman arasında geçiş yapmak zorunda kaldıysanız üretkenlik Enhancer Unity için Visual Studio Araçları. Unity için Visual Studio Araçları, Visual Studio 'dan çıkmadan çalışmanın devam etmesini kolaylaştırır.  
  
- **Unity Proje Gezgini** , Unity Düzenleyicisi 'nde görüntülenen aynı hiyerarşiyi kullanarak tüm Unity projenizi Visual Studio içinde görüntüler.  
  
- Unity konsol tümleştirmesi, Visual Studio 'nun hata penceresi içinde Unity konsolunun çıktısını görüntüler.  
  
- Visual Studio 'dan oyununuzda hata ayıklamayı başlatın; Unity 'ye geri dönmek için yalnızca F5 tuşuna basın.  
  
## <a name="superior-debugging"></a>Üstün hata ayıklama  
 Tek başına veya Unity düzenleyicisinde çalışıp çalışmadığını bağımsız olarak, betiklerinizde C# ve DLL 'lerde hata ayıklamak Için Visual Studio 'nun güçlü hata ayıklayıcısını Unity oyununuza bağlayın. Visual Studio 'da beklediğinizi tüm hata ayıklama özelliklerini kullanabilirsiniz.  
  
- Koşullu kesme noktaları da dahil olmak üzere kesme noktaları.  
  
- İzleme penceresinde karmaşık ifadeleri takip edin.  
  
- Değişkenleri ve bağımsız değişkenleri inceleyin ve değerlerini değiştirin.  
  
- Karmaşık nesnelerde ve veri yapılarında detaya gidin.  
  
  Hatta, ağınızdaki başka bir makinede çalışırken Unity oyununuzda hata ayıklayabilirsiniz.  
  
## <a name="productivity"></a>Üretkenlik  
 Visual Studio 'nun ' de C#kod yazma ve yeniden düzenleme verimliliğine ek olarak, Unity için Visual Studio Araçları Unity geliştiricileri için ek üretkenlik özellikleri sağlar.  
  
- Unity 'nin ShaderLab dili için sözdizimi renklendirme, hata haline gelmeden önce gölgelendiricilerde hata almanıza yardımcı olur. Yalnızca Visual Studio 'da ShaderLab dosyalarınızı açmanız yeterlidir.  
  
- MonoBehavior Sihirbazı, Unity davranışlarının bir listesine gözatmanızı sağlar ve alışık olabileceğiniz davranışlar için ortak kod oluşturur. CTRL + SHIFT + e tuşlarına basın.  
  
- En çok kullandığınız Unity davranışlarına alışdıktan sonra Hızlı MonoBehavior Sihirbazı bunları parmaklarınızın sağına koyar. CTRL + ALT + Q tuşlarına basın.  
  
- Visual Studio 'da Unity belgelerine erişin. Hakkında bilgi edinmek istediğiniz API çağrısını vurgulayın, sonra CTRL + ALT + M, CTRL + H tuşlarına basın.  
  
- Klavye kısayollarıyla tüm bu özelliklere ve daha fazlasına erişin.  
  
## <a name="visual-studio-tools-for-unity-api"></a>Unity API için Visual Studio Araçları  
 Unity için Visual Studio Araçları, belirtilen API 'Leri kullanarak davranışını özelleştirin ve genişletin.  
  
- Unity için Visual Studio Araçları, bir günlük geri çağırması kaydederek Unity konsolunun Visual Studio 'ya akışını sağlayabilir. Bilgileri günlüğe kaydetmek için kullandığınız düzenleyici betikleriniz varsa, iletilerinizi Visual Studio 'ya göndermek için aynı geri aramaya takabilirsiniz. Daha fazla bilgi için günlük geri çağırma örneğine bakın.  
  
- Unity stili geri çağırma ProjectFileGeneration kullanarak, Unity için Visual Studio Araçları proje dosyalarını nasıl üretkullanabileceğinizi değiştirebilirsiniz. Daha fazla bilgi için bkz. proje dosyası oluşturma örneği.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Unity giriş sayfası](https://unity.com/)
