---
title: Yük Testlerini Düzenleme
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- Load Test Editor
- load tests, Load Test Editor
ms.assetid: ba16ed02-137e-40bf-a4cb-45d87d922d37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 65cfdde84e0a0e2bb1aa28e9d4b96e2505a93a57
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665032"
---
# <a name="edit-load-tests"></a>Yük testlerini Düzenle

Yük testleri bir sunucuya aynı anda erişen birçok kullanıcının benzetimini yapmak için Web performans testlerini veya birim testlerini çalıştırır. Yük testi, uygulama stres ve performans verilerine erişmenizi sağlar. Yük testi, Kullanıcı yüklemeleri ve ağ türleri gibi çeşitli yük koşullarına benzemek için yapılandırılabilir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Yük testi *senaryolar*, *sayaç kümeleri*ve *çalışma ayarları*tarafından tanımlanır. Aşağıdaki çizimde [senaryolar](../test/edit-load-test-scenarios.md), [sayaç kümeleri](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)ve [çalışma ayarları](../test/load-test-run-settings-properties.md)arasındaki farklılıklar açıklanmaktadır:

![Yük testi mimarisi](../test/media/load_test_editor.png)

## <a name="software-requirements"></a>Yazılım gereksinimleri

Web performansı ve yük testi projeleri yalnızca Visual Studio Enterprise sürümünde kullanılabilir.

## <a name="edit-load-test-scenario-settings"></a>Yük testi senaryosu ayarlarını Düzenle

Bir senaryo, bir Kullanıcı grubunun bir sunucu uygulamasıyla nasıl etkileşime gireceğini modellemekte kullanılır. Bir senaryo, bir yük düzeninden, test karışımı modelinden, test karışımından, bir tarayıcı karışımından ve ağ karışımından oluşur. Bir yük testinin birden fazla senaryosu olabilir ve tek bir senaryo, Web performans testleri ve birim testleri içerebilir. Benzer ayarları birlikte gruplandırarak, bir senaryo benzer bir yapıdaki testleri gruplandırmanıza ve çalıştırmanıza olanak tanır.

Daha fazla bilgi için bkz. [Yük testi senaryolarını](../test/edit-load-test-scenarios.md) ve [Yük testi senaryosu özelliklerini](../test/load-test-scenario-properties.md)düzenleme.

## <a name="configure-and-manage-performance-counter-sets"></a>Performans sayacı kümelerini yapılandırma ve yönetme

Yük testleri, performans sayacı verilerini çözümlediğinizde kullanışlı olan teknoloji tarafından düzenlenen adlandırılmış sayaç kümeleri sağlar. Sayaç kümeleri yük testi, IIS, ASP.NET ve SQL içerir. **Yeni Yük Testi Sihirbazı**bir yük testi oluşturduğunuzda, yük testine dahil etmek üzere belirttiğiniz bilgisayarlar için önceden tanımlanmış ve önemli sayaçların ilk kümesi yapılandırılır. Sayaçlarınızı **Yük Testi Düzenleyicisi**yönetirsiniz.

Daha fazla bilgi için bkz. [bir yük testinde bilgisayarlar için sayaç kümelerini ve eşik kurallarını belirtme](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="configure-and-manage-load-test-run-settings"></a>Yük testi çalıştırma ayarlarını yapılandırma ve yönetme

Çalışma ayarları, bir yük testinin çalışma biçimini etkileyen özelliklerdir. Çalışma ayarları, **Özellikler** penceresindeki kategorilere göre düzenlenir.

Daha fazla bilgi için bkz. [Yük testi çalıştırma ayarlarını yapılandırma](../test/configure-load-test-run-settings.md) ve [test çalıştırması ayarlarını yükleme](../test/load-test-run-settings-properties.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi sonuçlarını çözümle](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Eşik Kuralı İhlallerini Çözümleme](../test/analyze-threshold-rule-violations-in-load-tests.md)