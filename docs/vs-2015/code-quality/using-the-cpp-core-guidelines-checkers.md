---
title: C++ Temel Yönergeleri denetleyicilerini kullanma | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: fffa4cec6a2bd7a340b90776ac20dc486f28045b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "84173580"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Temel Yönergeleri denetleyicilerini kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Temel Yönergeleri, C++ uzmanları ve tasarımcıları tarafından oluşturulan C++ ' da kodlama hakkında taşınabilir bir yönergeler, kurallar ve en iyi uygulamalar kümesidir.  Visual Studio artık kodunuzu C++ Temel Yönergeleri uyumlu olacak şekilde denetlemek ve iyileştirmeler önermek için kod analizi araçları için ek kurallar oluşturan eklenti paketlerini destekler.  
  
## <a name="the-c-core-guidelines-project"></a>C++ Temel Yönergeleri projesi  
 Bjarne Stroustrup ve diğerleri tarafından oluşturulan C++ Temel Yönergeleri, modern C++ ' ı güvenli ve etkili bir şekilde kullanmaya yönelik bir kılavuzdur. Yönergeler statik tür güvenliğini ve kaynak güvenliğini vurgular. Bu, dilin hata olasılığı olan kısımlarını ortadan kaldırmaya veya en aza indirmenin yollarını belirler ve kodunuzun daha basit ve daha iyi performans sağlamak için güvenilir bir yol sunar. Bu yönergeler standart C++ temeli tarafından korunur. Daha fazla bilgi edinmek için bkz. belge, [C++ temel yönergeleri](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)ve C++ temel yönergeleri belge proje dosyalarına [GitHub](https://github.com/isocpp/CppCoreGuidelines)'da erişin.  
  
 Microsoft, bir NuGet paketi kullanarak projelerinize ekleyebileceğiniz C++ Temel Denetimi kod analizi kural kümeleri yaparak C++ Temel Yönergeleri çabayı destekler. Paket Microsoft. CppCoreCheck olarak adlandırılmıştır ve ' de mevcuttur [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck) . Bu paket, güncelleştirme 1 ile en az Visual Studio 2015 yüklü olmasını gerektirir.  
  
 Paket, yalnızca üst bilgi kılavuz destek kitaplığı (GSL) olan bir bağımlılık olarak başka bir paket de yüklüyor. GSL, konumundaki GitHub 'da da kullanılabilir [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Kod çözümlemede C++ Temel Denetimi yönergeleri etkinleştirme  
 C++ Temel Denetimi Code Analysis araçları 'nı etkinleştirmek için, Visual Studio içinde denetlemek istediğiniz her C++ projesine Microsoft. CppCoreCheck NuGet paketini yükleyebilirsiniz.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Projenize Microsoft. CppCoreCheck paketi eklemek için  
  
1. **Çözüm Gezgini**' de, paketi eklemek Istediğiniz çözümde projenizin bağlam menüsünü açmak için sağ tıklayın. NuGet **paket yöneticisini**açmak Için **NuGet Paketlerini Yönet** ' i seçin.  
  
2. **NuGet Paket Yöneticisi** penceresinde Microsoft. CppCoreCheck öğesini arayın.  
  
    ![NuGet Paket Yöneticisi penceresi CppCoreCheck paketini gösterir](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Microsoft. CppCoreCheck paketini seçin ve ardından, kuralları projenize eklemek için **yükler** düğmesini seçin.  
  
   NuGet paketi projenize kod analizini etkinleştirdiğinizde çağrılan, projenize ek bir MSBuild. targets dosyası ekler. Bu. targets dosyası, C++ Temel Denetimi kurallarını Visual Studio Code Analysis aracına ek bir uzantı olarak ekler.  
  
   Projeniz için **Özellik sayfaları** Iletişim kutusunun **Kod Analizi** bölümünde **derleme üzerinde Kod analizini etkinleştir** onay kutusunu seçerek projenizde kod analizini etkinleştirebilirsiniz.  
  
   ![Kod Analizi genel ayarları için özellik sayfası](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Temel Denetimi kuralları, kod analizi etkinleştirildiğinde çalışan varsayılan kural kümelerinin bir parçası olur. C++ Temel Denetimi kuralları geliştirme aşamasındadır, bazı kurallar tüm kodda kullanıma hazırlanmayabilir, ancak geliştirme sırasında bilgilendirici olabilir. Bu kurallar deneysel olarak serbest bırakılır. Yayınlanan veya deneysel kuralların projenizin özelliklerinde çalıştırılıp çalıştırılmayacağını seçebilirsiniz.  
  
   ![Kod Analizi uzantıları ayarları için özellik sayfası](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   C++ Temel Denetimi kural kümelerini etkinleştirmek veya devre dışı bırakmak için, projeniz için **Özellik sayfaları** iletişim kutusunu açın. **Yapılandırma özellikleri**altında, **Kod Analizi**, **Uzantılar**' ı genişletin. **C++ temel denetimi (serbest bırakıldı)** veya **C++ temel denetimi (deneysel)** seçeneğini etkinleştir ' ın yanındaki açılan denetimde **Evet** veya **Hayır**' ı seçin. Değişikliklerinizi kaydetmek için **Tamam ' ı** veya **Uygula** ' yı seçin.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Türleri, sınırları ve ömürleri denetleyin  
 C++ Temel Denetimi paketi şu anda [tür güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [sınır güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)ve [ömür güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profilleri için kareler içerir.  
  
 C++ Temel Denetimi kuralların bulabileceği sorunların türüne bir örnek aşağıda verilmiştir:  
  
```cpp  
// CoreCheckExample.cpp  
// Add CppCoreCheck package and enable code analysis in build for warnings.  
  
int main()  
{  
    int arr[10];           // warning C26494  
    int* p = arr;          // warning C26485  
  
    [[gsl::suppress(bounds.1)]] // This attribute suppresses Bounds rule #1  
    {  
        int* q = p + 1;    // warning C26481 (suppressed)  
        p = q++;           // warning C26481 (suppressed)  
    }  
  
    return 0;  
}  
```  
  
 Bu örnek C++ Temel Denetimi kuralların bulabileceği uyarıların birkaçını gösterir:  
  
- C26494, kural türü. 5: her zaman bir nesne başlatın.  
  
- C26485, kural sınırlardır. 3: bir dizi işaretçiden işaretçiye sınır yok.  
  
- C26481 kural sınırları. 1: işaretçi aritmetiği kullanmayın. Bunun yerine `span` kullanın.  
  
  Bu kodu derlerken C++ Temel Denetimi Code Analysis kural kümeleri yüklenip etkinleştirilirse, ilk iki uyarı çıkışlardır, ancak üçüncüsü bastırılır. Örnek koddan derleme çıktısı aşağıda verilmiştir:  
  
**1>------derleme başladı: proje: CoreCheckExample, yapılandırma: hata ayıklama Win32--**  
**----**  
**1> CoreCheckExample. cpp**  
**1> CoreCheckExample. vcxproj-> C:\users\username\k\studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1> CoreCheckExample. vcxproj-> C:\users\username\k\studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (tam PDB)**  
**c:\users\username\k\studio 2015 \ projelericorecheckexample\coreche**  
**ckexample\corecheckexample.exe (6): Warning C26494: ' ARR ' değişkeni bir unınitializ**  
**Konik. Her zaman bir nesne başlatın. (Type. 5: https: \/ /Go.Microsoft.com/fwlink/p/?link**  
**ID = 620421)**  
**c:\users\username\k\studio 2015 \ projelericorecheckexample\coreche**  
**ckexample\corecheckexample.exe (7): uyarı C26485: Ifade ' ARR ': hiçbir dizi yok**  
**işaretçi Decay. (sınır. 3: https: \/ /Go.Microsoft.com/fwlink/p/?LinkId=620415)**  
**= = = = = = = = = = Build: 1 başarılı, 0 başarısız, 0 güncel, 0 ile atlanan = = = = = =** 

C++ Temel Yönergeleri daha iyi ve daha güvenli bir kod yazmanıza yardımcı olur. Ancak, bir kuralın veya profilin uygulanmaması gereken bir örneğiniz varsa, doğrudan kodda görüntülenmesini kolaydır. `gsl::suppress`Aşağıdaki kod bloğunda bir kuralın ihlal edildiğini ve raporlanmasını C++ temel denetimi önlemek için özniteliğini kullanabilirsiniz. Belirli kuralları bastırmak için tek tek deyimleri işaretleyebilirsiniz. `[[gsl::suppress(bounds)]]`Belirli bir kural numarası dahil etmeden yazarak tüm sınır profilini de gizleyebilirsiniz.  
  
## <a name="use-the-guideline-support-library"></a>Kılavuz desteği kitaplığını kullanma  
 Microsoft. CppCoreCheck NuGet paketi Microsoft 'un kılavuz destek kitaplığı (GSL) uygulamasını içeren bir paket de yüklüyor. GSL, ' de tek başına biçimde de kullanılabilir [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl) . Bu kitaplık, temel yönergeleri izlemek istediğinizde yararlıdır. GSL, hataya açık olan yapıları daha güvenli alternatifler ile değiştirmenize olanak tanıyan tanımlar içerir. Örneğin, bir `T*, length` parametre çiftini `span<T>` türüyle değiştirebilirsiniz. GSL açık kaynaktır, bu nedenle kitaplık kaynaklarına, açıklamaya veya katkıda bulunmak için projeye göz atın [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL) .
