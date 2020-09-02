---
title: Komut satırı parametrelerini kullanarak Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- command-line parameters
- switches
- command prompt
ms.assetid: 480f3cb4-d873-434e-a8bf-82cff7401cf2
caps.latest.revision: 10
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a3fe0233f08f33535be4b02cc06c29d919d75169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180258"
---
# <a name="use-command-line-parameters-to-install-visual-studio"></a>Visual Studio'yu Yüklemek için Satır İçi Parametreleri Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [Visual Studio 'yu yüklemek için komut satırı parametrelerini kullanma](/visualstudio/install/use-command-line-parameters-to-install-visual-studio).

Visual Studio 2015 'yi bir komut isteminden yüklerken aşağıdaki komut satırı parametrelerini (anahtarlar olarak da bilinir) kullanabilirsiniz.

> [!NOTE]
> Önyükleyici dosyasını değil gerçek yükleyiciyi kullandığınızdan emin olun. Örneğin, **`vs_enterprise.exe`** Vs_enterprise_*GUID*. exe yerine kullandığınızdan emin olun. Bir yükleyiciyi [My.VisualStudio.com](https://my.visualstudio.com/downloads?q=visual%20studio%20enterprise%202015)adresinden indirebilirsiniz.

## <a name="list-of-command-line-parameters"></a>Komut satırı parametrelerinin listesi

Visual Studio komut satırı parametreleri büyük/küçük harfe duyarlı değildir.

|Parametre|Açıklama|
|---------------|-----------------|
|**/?**<br /><br /> **/Help**<br /><br /> **/h**|Komut satırı parametrelerini görüntüler.|
|**/AddRemoveFeatures**|Yüklü ürüne hangi özelliklerin ekleneceğini veya üründen hangi özelliklerin kaldırılacağını belirtir.|
|**/Adminfile** *AdminDeployment.xml*|Visual Studio'yu, yönetimsel yükleme için belirttiğiniz veri dosyasını kullanarak yükler.|
|**/ChainingPackage** *paketleme liname*|Bu paketi hangi paketin zincirlediğini belirtir. Ayrıca, bir müşteri geliştirme deneyimi kohortu belirtmek için de kullanılabilir.|
|**/CreateAdminFile \<filename>**|/AdminFile ile kullanılabilecek bir denetim dosyası oluşturma konumunu belirtir|
|**/Customınstallpath** *InstallationDirectory*|Tüm yeniden hedeflenebilir paketleri belirttiğiniz dizine yükler.|
|**/ForceRestart**|Yüklemeden sonra her zaman bilgisayarı yeniden başlatır.|
|**/full**|Tüm ürün özelliklerini yükler.|
|**/InstallSelectableItems \<item name 1> [; \<item name 2> ]**|Yükleyici sihirbazının seçim ekranında denetlenecek seçim ağacı öğelerinin listesi.|
|**/l**<br /><br /> **/Log** *dosya adı*|Günlük dosyası için bir konum belirtir.|
|**/Layout** *dizini*|Yükleme medyasındaki dosyaları belirttiğiniz dizine kopyalar.|
|**/NoCacheOnlyMode**|Paket önbelleğinin önceden doldurulmasını engeller.|
|**/NoRefresh**|Gerekli ya da önerilen güncelleştirilmiş sürümler için bu ürünün daha yeni sürümlerinin denetlenmesini engeller.|
|**/norestart**|Yükleme uygulamasının, yükleme sırasında veya yüklemeden sonra bilgisayarı yeniden başlatmasını engeller. Aranacak dönüş kodları için [Visual Studio Yönetici Kılavuzu ' nu](../install/visual-studio-administrator-guide.md) geri dönüş kodları bölümüne bakın.|
|**/NoWeb**|Internet'ten yüklemeyi engeller.|
|**/Overdefeeduri \<path to feed file>**|Yazılım öğelerini açıklayan yerel, dış akışın yolu|
|**/ProductKey**<br /><br /> *ProductKey*|Tire içermeyen ve en fazla 25 karakter içeren özel bir ürün anahtarı ayarlar.|
|**/PromptRestart**|Bilgisayarı yeniden başlatmadan önce kullanıcıya sorar.|
|**anahtarın**<br /><br /> **/**<br /><br /> **sn**<br /><br /> **/silent**|Yükleme uygulaması için kullanıcı arabirimini (UI) bastırır. Visual Studio zaten yüklüyse ve bunun dışında bir parametre belirtmezseniz, yükleme uygulaması Bakım modunda çalışır.|
|**/QB**<br /><br /> **/passive**|İlerleme durumunu gösterir ancak kullanıcı girişini beklemez.|
|**/Repair**|Visual Studio'yu onarır.|
|**/SuppressRefreshPrompt**|Yükleme sihirbazında kullanılabilir güncelleştirme iletişim kutusunun görüntülenmesini önler, böylece Yükleme Sihirbazı gerekli veya önerilen güncelleştirilmiş sürümleri otomatik olarak kabul eder.|
|**p**<br /><br /> **/Uninstall**|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]'ı kaldırır.|
|**/Uninstall/Force**<br /><br /> **/u/Force**|Visual Studio'yu ve diğer ürünlerle paylaşılan tüm özellikleri kaldırır. **Uyarı:**  Bu parametreyi kullanırsanız, aynı bilgisayarda yüklü diğer ürünler düzgün çalışmamaya meyebilir.|

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Yönetici Kılavuzu](../install/visual-studio-administrator-guide.md)