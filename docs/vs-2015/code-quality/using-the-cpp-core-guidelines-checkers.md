---
title: C++ Temel kılavuz denetleyicilerini kullanma | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: a2098fd9-8334-4e95-9b8d-bc3da689d9e3
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 946b46bfb5101154832e10b61cd861b0c104dc14
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77275293"
---
# <a name="using-the-c-core-guidelines-checkers"></a>C++ Temel Yönergeleri denetleyicilerini kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C++ Temel yönergeler, uzmanlar ve tasarımcılar tarafından C++ C++ oluşturulan kodlama hakkında taşınabilir bir yönergeler, kurallar ve en iyi uygulamalar kümesidir.  Visual Studio artık kodunuzu C++ temel yönergelerle uyumlu olacak şekilde denetlemek ve iyileştirmeler önermek için kod analizi araçları için ek kurallar oluşturan eklenti paketlerini destekler.  
  
## <a name="the-c-core-guidelines-project"></a>C++ Temel yönergeler projesi  
 Bjarne Stroustrup ve diğerleri tarafından oluşturulan C++ temel yönergeler, modern C++ bir şekilde güvenli ve etkili bir şekilde kullanılması için bir kılavuzdur. Yönergeler statik tür güvenliğini ve kaynak güvenliğini vurgular. Bu, dilin hata olasılığı olan kısımlarını ortadan kaldırmaya veya en aza indirmenin yollarını belirler ve kodunuzun daha basit ve daha iyi performans sağlamak için güvenilir bir yol sunar. Bu yönergeler standart C++ temel tarafından korunur. Daha fazla bilgi edinmek için, bkz. belge, [ C++ temel yönergeler](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines)ve GitHub C++ 'daki temel yönergeler belge proje dosyalarına [](https://github.com/isocpp/CppCoreGuidelines)erişin.  
  
 Microsoft, C++ bir NuGet paketi kullanarak projelerinize C++ ekleyebileceğiniz temel denetim kodu analiz kuralı kümeleri oluşturarak temel yönergeler çabalarını destekler. Paketin adı Microsoft. CppCoreCheck olarak adlandırılmıştır ve [https://www.nuget.org/packages/Microsoft.CppCoreCheck](https://www.nuget.org/packages/Microsoft.CppCoreCheck)adresinden kullanılabilir. Bu paket, güncelleştirme 1 ile en az Visual Studio 2015 yüklü olmasını gerektirir.  
  
 Paket, yalnızca üst bilgi kılavuz destek kitaplığı (GSL) olan bir bağımlılık olarak başka bir paket de yüklüyor. GSL, [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)'de GitHub 'da da kullanılabilir.  
  
## <a name="enable-the-c-core-check-guidelines-in-code-analysis"></a>Kod çözümlemede C++ çekirdek denetim yönergelerini etkinleştirme  
 C++ Çekirdek denetimi kod analizi araçlarını etkinleştirmek Için, Visual Studio içinde denetlemek istediğiniz her C++ bir projeye Microsoft. Cppcorecheck NuGet paketini yükleyebilirsiniz.  
  
#### <a name="to-add-the-microsoftcppcorecheck-package-to-your-project"></a>Projenize Microsoft. CppCoreCheck paketi eklemek için  
  
1. **Çözüm Gezgini**' de, paketi eklemek Istediğiniz çözümde projenizin bağlam menüsünü açmak için sağ tıklayın. NuGet **paket yöneticisini**açmak Için **NuGet Paketlerini Yönet** ' i seçin.  
  
2. **NuGet Paket Yöneticisi** penceresinde Microsoft. CppCoreCheck öğesini arayın.  
  
    ![NuGet Paket Yöneticisi penceresi CppCoreCheck paketini gösterir](../code-quality/media/cppcorecheck-nuget-window.PNG "CPPCoreCheck_Nuget_Window")  
  
3. Microsoft. CppCoreCheck paketini seçin ve ardından, kuralları projenize eklemek için **yükler** düğmesini seçin.  
  
   NuGet paketi projenize kod analizini etkinleştirdiğinizde çağrılan, projenize ek bir MSBuild. targets dosyası ekler. Bu. targets dosyası, Visual C++ Studio kod analizi aracına ek bir uzantı olarak çekirdek denetim kuralları ekler.  
  
   Projeniz için **Özellik sayfaları** Iletişim kutusunun **Kod Analizi** bölümünde **derleme üzerinde Kod analizini etkinleştir** onay kutusunu seçerek projenizde kod analizini etkinleştirebilirsiniz.  
  
   ![Kod Analizi genel ayarları için özellik sayfası](../code-quality/media/cppcorecheck-codeanalysis-general.png "CPPCoreCheck_CodeAnalysis_General")  
  
   C++ Çekirdek denetim kuralları, kod analizi etkinleştirildiğinde çalışan varsayılan kural kümelerinin bir parçası haline gelir. C++ Çekirdek denetim kuralları geliştirme aşamasında olduğundan, bazı kurallar tüm kodda kullanıma hazırlanmayabilir, ancak geliştirme sırasında bilgilendirici olabilir. Bu kurallar deneysel olarak serbest bırakılır. Yayınlanan veya deneysel kuralların projenizin özelliklerinde çalıştırılıp çalıştırılmayacağını seçebilirsiniz.  
  
   ![Kod Analizi uzantıları ayarları için özellik sayfası](../code-quality/media/cppcorecheck-codeanalysis-extensions.png "CPPCoreCheck_CodeAnalysis_Extensions")  
  
   C++ Çekirdek denetimi kural kümelerini etkinleştirmek veya devre dışı bırakmak için, projeniz Için **Özellik sayfaları** iletişim kutusunu açın. **Yapılandırma özellikleri**altında, **Kod Analizi**, **Uzantılar**' ı genişletin. **Çekirdek C++ denetimini etkinleştir (serbest bırakıldı)** veya **çekirdek denetimini etkinleştir C++ (deneysel)** seçeneğinin yanındaki aşağı açılan denetimde **Evet** veya **Hayır**' ı seçin. Değişikliklerinizi kaydetmek için **Tamam ' ı** veya **Uygula** ' yı seçin.  
  
## <a name="check-types-bounds-and-lifetimes"></a>Türleri, sınırları ve ömürleri denetleyin  
 C++ Çekirdek denetim paketi şu anda [tür güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-type), [sınır güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-bounds)ve [ömür güvenliği](http://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines#SS-lifetime) profilleri için damalı içerir.  
  
 C++ Temel denetim kurallarının bulabileceği sorunların türüne bir örnek aşağıda verilmiştir:  
  
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
  
 Bu örnek, C++ çekirdek denetim kurallarının bulabileceği bazı uyarıları gösterir:  
  
- C26494, kural türü. 5: her zaman bir nesne başlatın.  
  
- C26485, kural sınırlardır. 3: bir dizi işaretçiden işaretçiye sınır yok.  
  
- C26481 kural sınırları. 1: işaretçi aritmetiği kullanmayın. Bunun yerine `span` kullanın.  
  
  Bu kodu C++ derlerken çekirdek denetim kodu analizi RuleSets 'ler yüklenip etkinleştirildiyse, ilk iki uyarı çıkışlardır, ancak üçüncüsü bastırılır. Örnek koddan derleme çıktısı aşağıda verilmiştir:  
  
**1 >------derleme başladı: proje: CoreCheckExample, yapılandırma: hata ayıklama Win32--**  
**----**  
**1 > CoreCheckExample. cpp**  
**1 > CoreCheckExample. vcxproj-> C:\users\username\k\studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.exe**  
**1 > CoreCheckExample. vcxproj-> C:\users\username\k\studio 2015 \ P**  
**rojects\CoreCheckExample\Debug\CoreCheckExample.pdb (tam PDB)**  
**c:\users\username\k\studio 2015 \ projelericorecheckexample\coreche**  
**ckexample\corecheckexample.exe (6): Warning C26494: ' ARR ' değişkeni bir unınitializ**  
**Ed. her zaman bir nesne başlatın. (Type. 5: https://go.microsoft.com/fwlink/p/?Link**  
**ID = 620421)**  
**c:\users\username\k\studio 2015 \ projelericorecheckexample\coreche**  
**ckexample\corecheckexample.exe (7): uyarı C26485: Ifade ' ARR ': hiçbir dizi yok**  
**işaretçi Decay. (sınır. 3: https://go.microsoft.com/fwlink/p/?LinkID=620415)**  
**= = = = = = = = = = Build: 1 başarılı, 0 başarısız, 0 güncel** , 0 ile atlanan = = = = = = Temel C++ yönergeler, daha iyi ve daha güvenli bir kod yazmanıza yardımcı olur. Ancak, bir kuralın veya profilin uygulanmaması gereken bir örneğiniz varsa, doğrudan kodda görüntülenmesini kolaydır. Aşağıdaki kod bloğunda bir kuralın ihlalini algılamasını C++ ve raporlanmasını önlemek için `gsl::suppress` özniteliğini kullanabilirsiniz. Belirli kuralları bastırmak için tek tek deyimleri işaretleyebilirsiniz. Belirli bir kural numarası dahil etmeden `[[gsl::suppress(bounds)]]` yazarak tüm sınır profillerinin de görüntülenmesini sağlayabilirsiniz.  
  
## <a name="use-the-guideline-support-library"></a>Kılavuz desteği kitaplığını kullanma  
 Microsoft. CppCoreCheck NuGet paketi Microsoft 'un kılavuz destek kitaplığı (GSL) uygulamasını içeren bir paket de yüklüyor. GSL, [http://www.nuget.org/packages/Microsoft.Gsl](https://www.nuget.org/packages/Microsoft.Gsl)tek başına biçimde de kullanılabilir. Bu kitaplık, temel yönergeleri izlemek istediğinizde yararlıdır. GSL, hataya açık olan yapıları daha güvenli alternatifler ile değiştirmenize olanak tanıyan tanımlar içerir. Örneğin, parametrelerin `T*, length` çiftini `span<T>` türüyle değiştirebilirsiniz. GSL açık kaynaktır, bu nedenle kitaplık kaynaklarına, açıklamaya veya katkıda bulunmak istiyorsanız proje [https://github.com/Microsoft/GSL](https://github.com/Microsoft/GSL)bulunabilir.
