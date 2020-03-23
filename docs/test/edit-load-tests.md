---
title: Yük Testlerini Düzenleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c61c13f6a9eca416a52221ba9da37be820dd4b89
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593232"
---
# <a name="edit-load-tests"></a>Yük testlerini edit

Yük testleri, aynı anda bir sunucuya erişen birçok kullanıcıyı simüle etmek için web performans testleri veya birim testleri çalıştırın. Yükleme testi, uygulama stresi ve performans verilerine erişmenizi sağlar. Yük testi, kullanıcı yükleri ve ağ türleri gibi çeşitli yük koşullarını taklit edecek şekilde yapılandırılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi *senaryolar,* *sayaç kümeleri*ve *çalıştırma ayarları*yla tanımlanır. Aşağıdaki resimde [senaryolar,](../test/edit-load-test-scenarios.md) [sayaç kümeleri](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)ve [çalıştırma ayarları](../test/load-test-run-settings-properties.md)arasındaki farklar açıklanmaktadır:

![Yük Testi Mimarisi](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Yazılım gereksinimleri

Web performansı ve yük testi projeleri yalnızca Visual Studio'nun Enterprise sayısında mevcuttur.

## <a name="edit-load-test-scenario-settings"></a>Yük testi senaryo ayarlarını değiştir

Senaryo, bir kullanıcı grubunun bir sunucu uygulamasıyla nasıl etkileşimde olduğunu modellemek için kullanılır. Bir senaryo bir yük deseni, bir test karışımı modeli, bir test karışımı, bir tarayıcı karışımı ve ağ karışımı oluşur. Bir yük testi birden fazla senaryoya sahip olabilir ve tek bir senaryo web performans testleri ve birim testleri içerebilir. Benzer ayarları birlikte gruplandırmak, bir senaryo, benzer türdeki testleri gruplandırmanızı ve çalıştırmanızı sağlar.

Daha fazla bilgi için bkz: Yük testi senaryolarını ve [Yük testi senaryo özelliklerini](../test/load-test-scenario-properties.md) [edit.](../test/edit-load-test-scenarios.md)

## <a name="configure-and-manage-performance-counter-sets"></a>Performans sayıcı kümelerini yapılandırma ve yönetme

Yük testleri, performans sayacı verilerini çözümlediğinizde yararlı olan, teknoloji tarafından düzenlenen adlandırılmış sayaç kümeleri sağlar. Sayaç kümeleri Yük Testi, IIS, ASP.NET ve SQL içerir. **Yeni Yük Testi Sihirbazı**ile bir yük testi oluşturduğunuzda, yük testine dahil etmek üzere belirttiğiniz bilgisayarlar için önceden tanımlanmış ve önemli sayaçlardan oluşan bir başlangıç kümesi yapılandırılır. Yük Testi Düzenleyicisi'nde sayaçlarınızı yönetirsiniz. **Load Test Editor**

Daha fazla bilgi için [bkz.](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)

## <a name="configure-and-manage-load-test-run-settings"></a>Yük testi çalıştırma ayarlarını yapılandırma ve yönetme

Çalıştırma ayarları, yük testinin çalışma şeklini etkileyen özelliklerdir. Çalıştırma ayarları **Özellikler** penceresindeki kategorilere göre düzenlenir.

Daha fazla bilgi için bkz: [Yük testi çalıştır ayarlarını yapılandırVe](../test/configure-load-test-run-settings.md) [test çalıştırma ayarlarını yükleyin.](../test/load-test-run-settings-properties.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını analiz edin](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Eşik kural ihlallerini çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)
