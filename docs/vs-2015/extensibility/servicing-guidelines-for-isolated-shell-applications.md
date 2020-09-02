---
title: Yalıtılmış kabuk uygulamaları için bakım yönergeleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio Shell integrated mode, serviceability
- Shell integrated mode [Visual Studio], serviceability
ms.assetid: 747d1a47-b8b3-4e8b-93c0-768724be48f2
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 093690c293ff6857eedc50d5eccc793d7d5bb114
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68159275"
---
# <a name="servicing-guidelines-for-isolated-shell-applications"></a>Yalıtılmış Kabuk Uygulamaları için Hizmet Sunma Yönergeleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir Visual Studio yalıtılmış kabuk uygulamasını dağıttığınızda, yüklendikten sonra uygulamanız için yazılım güncelleştirmeleri sağlayabilmelisiniz. Bunu yapmak için, uygulamanızı bir Microsoft Installer (MSI) dosyası kullanarak kurmanız gerekir. Bu tür bir yükleme, Microsoft tarafından sunulan yazılım güncelleştirmelerinin Web 'den yeniden dağıtılması ve müşterilerinizin özel müdahale olmadan müşterileriniz tarafından tüketilmesi için izin verir.  
  
## <a name="servicing-requirements"></a>Bakım gereksinimleri  
 Yükleme programınızın aşağıdaki üç ölçütü karşıladığından emin olduktan sonra, yalıtılmış Kabuk yüklemenizin güncelleştirmelere izin verebilir şekilde emin olabilirsiniz.  
  
### <a name="redistribute-by-using-an-msi"></a>MSI kullanarak yeniden dağıtma  
 Bir MSI ürün kimliğini koruyacağından ve uygulamanın istemci bilgisayarda fiziksel bir konuma sahip olduğundan emin olduğundan, uygulamanızı yeniden dağıtmak için bir MSI kullanmanız gerekir. Birleştirme modülleri (. msm dosyaları) bu tür izinleri sağlamaz ve kullanılmamalıdır.  
  
### <a name="accounting-for-custom-actions"></a>Özel eylemler için hesaplama  
 Özel eylemler bir yükleyici programında standart olmayan yükleme yönergelerinden değildir. Özel Eylemler, dosya konumları, kayıt defteri ayarları, Kullanıcı ayarları veya diğer yükleme öğeleri gibi parametreleri değiştirir. Özel eylemler verileri yükleme sırasında işleyebilir.  
  
 Bir yükleme programında özel eylemler kullandığınızda, her yükleme zamanı özel eyleminin, Kullanıcı uygulamayı kaldırırken eylemi geri almak için karşılık gelen özel bir eyleme sahip olması gerekir. Yükleme programınız ilgili kaldırma özel eylemini sağlayamazsa, uygulamanızı kaldırmak kısmen yüklenmiş olarak bırakır.  
  
- Yazılım güncelleştirmeleri bu sürümleri veya karma değerleri değiştirirken, bir dosyanın veya karma değerlerin belirli bir sürümünü kullanan özel bir eylem başarısız olur. Bu durumda, Özel eyleminiz bu değerleri el ile güncelleştirmeniz gerekir. Bir dosya veya karma değer sürümleri ürün sürümleri arasında paylaşılmışsa ek bir sorun oluşur. Mümkün olduğunda bu bağımlılığı önleyin.  
  
### <a name="accounting-for-shared-files"></a>Paylaşılan dosyalar için hesaplama  
 Paylaşılan dosyalar aynı ada sahiptir ve birden çok ürünle aynı konuma yüklenir. Bu ürünler sürüm, stok tutma birimi (SKU) veya her ikisi de farklılık gösterebilir ve ürünler belirli bir bilgisayarda birlikte bulunabilir. Ancak, paylaşılan dosyalar çeşitli nedenlerle bakım sorunları oluşturur:  
  
- Bir uygulamaya yönelik bir güncelleştirme, güncelleştirilmemiş ikinci bir uygulama tarafından kullanılan bir dosyanın sürümünü değiştirebileceğinden, paylaşılan dosyaların güncelleştirilmesi uygulama uyumluluk sorunlarına neden olabilir. Paylaşılan dosyalara dosya sayısı başvurularını paylaşan ürünlere yönelik yükleyiciler. Bu nedenle, bir ürünün kaldırılması, yüklü örnek sayısının ötesinde paylaşılan dosyaları etkilemez.  
  
- Hızlı çözüm Mühendisliği (QFE) yükleyicisi, dosyaların sürümlerini QFE yükleyicisinin hizmet verdiği ürünlerin sürümlerine geri alır. Bu işlem, güncelleştirilmiş bir paylaşılan dosyayı almış olan bir uygulamayı kesintiye karşı kesintiye karşı keser.
