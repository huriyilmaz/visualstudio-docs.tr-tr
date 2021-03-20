---
title: Codespace ile Visual Studio (Önizleme)
description: Visual Studio IDE 'yi Windows geliştirme için GitHub Codespaces ile kullanma hakkında bilgi edinin.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: add43a5d130d8938193774d50bb643f48ecc3f8c
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104673053"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Visual Studio 'Yu bir codespace ile kullanma (Önizleme)

> [!Important] 
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için [Geliştirici topluluğu forumumuza](https://developercommunity.visualstudio.com/home) dahil etmeniz önerilir. 

Visual Studio, GitHub Codespaces 'da geliştirme için harika destek içerir. Bir codespace oluşturup bu alana bağlanabilir ve Visual Studio 'nun tam gücünden uzak, barındırılan bir ortamda projeleriniz üzerinde çalışabilirsiniz. Kaynak kodunuz ve araçlarınız bir codespace içinde olsa da, derleme ve hata ayıklama bulutu bulutta gerçekleşse de, yerel olarak çalıştıkmiş gibi geliştirme deneyiminiz hızlı ve duyarlı bir şekilde ücretsizdir.

> [!NOTE]
> Bu makale, GitHub Codespaces 'a bağlanmak için özellikle Visual Studio 'Yu kullanmayı açıklamaktadır. [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) veya [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) belgelerindeki diğer istemcilerle bir codespace 'e bağlanma hakkında bilgi edinebilirsiniz.

> [!NOTE]
> [Visual Studio 2019 Preview](https://aka.ms/vspreview) zaten yüklü değilse, [VisualStudio.Microsoft.com](https://aka.ms/vspreview)adresinden indirebilirsiniz.

## <a name="enable-connect-to-github-codespaces"></a>GitHub Codespaces 'a bağlanmayı etkinleştir

Visual Studio 2019 Preview ile GitHub Codespaces 'a bağlanmak varsayılan olarak etkin değildir, bu nedenle önce Önizleme özellikleri seçeneğini etkinleştirmeniz gerekir.

1. Visual Studio 2019 önizlemesinde,   >  Seçenekler iletişim kutusunu açmak için Araçlar **Seçenekler** menü öğesini kullanın.

2. **Ortam** altında **Önizleme özellikleri** ' ni seçin ve **GitHub Codespaces** Önizlemesi ' ne bağlan ' ı işaretleyin.

   ![GitHub Codespaces önizleme özelliğinin bağlantısını denetleyin](media/connect-to-github-codespaces-preview-feature.png)

3. Özelliğin kullanılabilmesi için Visual Studio 'Yu yeniden başlatmanız gerekir.

## <a name="create-a-codespace"></a>Codespace oluşturma

Zaten bir codespace yoksa, Visual Studio 'dan bir tane oluşturabilirsiniz.

1. Visual Studio 'Yu başlattığınızda, başlangıç penceresinde "kullanmaya başlayın" bölümünün altındaki bir **codespace düğmesine Bağlan** gösterilir.

   ![Codespace 'e bağlanma ile Visual Studio başlangıç penceresi](media/visual-studio-start-window.png)

2. **Bir codespace 'e Bağlan** ' ı seçtiğinizde, GitHub 'da oturum açmanız istenir. Zaten yoksa bir GitHub hesabı da oluşturabilirsiniz.

   ![Visual Studio GitHub 'da oturum açın](media/visual-studio-sign-in-to-github.png)

   **GitHub 'Da oturum aç**' ı seçtikten sonra çevrimiçi GitHub oturum açma iş akışını izleyin.

3. Hiç bir codespace oluşturmadıysanız, sizden bir tane oluşturmanız istenir.

   "Codespace details" bölümünde, bir **Depo URL 'si** sağlamanız gerekir. GitHub Codespaces, belirtilen depoyu oluşturma sırasında codespace 'e kopyalar.

   Ayrıca, **örnek türünü** değiştirebilir ve zaman aşımından **sonra** , açılan listeleri aracılığıyla askıya alabilirsiniz. Codespace ayrıntılarını ayarladıktan sonra **Oluştur ve Bağlan** düğmesini seçin.

   ![Visual Studio codespace ayrıntıları](media/visual-studio-codespace-details.png)

   GitHub Codespaces, codespace hazırlanıyor ve Visual Studio 'yu açarak codespace hazırlanmaya başlar.

   Codespace adı, menü çubuğundaki uzak göstergede görüntülenir.

   ![EShopOnWeb Repository codespace 'e bağlı Visual Studio](media/visual-studio-eshoponweb-codespace.png)

4. Yerel olarak çalışırken olduğu gibi, Visual Studio 'Yu kullanmaya başlayın. Deneyebileceğiniz şeyler:

   * Kaynak koduna gözatamazsınız.
   * Bir çözüm dosyası seçin ve çözümü oluşturun (**Ctrl + Shift + B**).
   * Kaynak dosyada bir kesme noktası ayarlayın ve **F5** tuşuna basarak uygulamayı hata ayıklayıcıda başlatın.
   * Değişiklikleri yapın ve deponuza işleyin.   

> [!NOTE]
> Şu anda, GitHub [codespaces portalı](https://github.com/codespaces)aracılığıyla Visual Studio Için GitHub codespaces oluşturmamalıdır. Yalnızca Visual Studio 'Yu kullanarak oluşturabilirsiniz.

## <a name="connect-to-a-codespace"></a>Codespace 'e bağlanma

Codespace 'i oluşturduktan sonra, codespace 'i doğrudan Visual Studio 'dan açabilirsiniz.

1. Visual Studio 'Yu başlattığınızda, başlangıç penceresinde "kullanmaya başlayın" bölümünün altındaki bir **Codespace düğmesine Bağlan** gösterilir.

   ![Codespace 'e bağlanma ile Visual Studio başlangıç penceresi](media/visual-studio-start-window.png)

   Zaten Visual Studio kullanıyorsanız,   >  **bir codespace** menü öğesini kullanarak dosya bağla ' yı kullanabilirsiniz.

   ![Visual Studio dosyası bir codespace menü öğesine Bağlan](media/visual-studio-file-connect-to-codespace.png)

2. **Bir codespace 'e Bağlan**' ı seçin. Henüz yapmadıysanız, GitHub 'da oturum açmanız istenir.

3. Daha sonra, GitHub codespaces ' ı sağ panelde görüntülenen ayrıntılarla birlikte görürsünüz.

   ![Kullanılabilir GitHub kod alanlarını ve ayrıntılarını görüntüleyen Visual Studio](media/visual-studio-connect-codespace.png)

   Azure DevOps deposunu klonlanan tüm kod alanları, GitHub 'ın Codespaces sayfasında değil yalnızca Visual Studio 'da görünür.

4. Bir codespace seçin ve **Bağlan** düğmesini seçin. Codespace askıya alınmışsa, yeniden başlatılır ve Visual Studio bu codespace 'e bağlı olarak açılır.

   Codespace adı, menü çubuğundaki uzak göstergede görüntülenir.

   ![EShopOnWeb Repository codespace 'e bağlı Visual Studio](media/visual-studio-eshoponweb-codespace.png)

5. Yerel olarak çalışırken olduğu gibi, Visual Studio 'Yu kullanmaya başlayın. Deneyebileceğiniz şeyler:

   * Kaynak koduna gözatamazsınız.
   * Bir çözüm dosyası seçin ve çözümü oluşturun (**Ctrl + Shift + B**).
   * Kaynak dosyada bir kesme noktası ayarlayın ve **F5** tuşuna basarak uygulamayı hata ayıklayıcıda başlatın.
   * Değişiklikleri yapın ve deponuza işleyin.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Ayrıca bkz.

* [GitHub Codespaces nedir?](codespaces-overview.md)
* [Codespace 'i özelleştirme](customize-codespaces.md)
* [Desteklenen Visual Studio özellikleri](supported-features-codespaces.md)
