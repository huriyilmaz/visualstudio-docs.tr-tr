---
title: Yük testi için Dağıtım Gecikmesine Dağıtım Uygulama
description: Bir yük testi için Dağıtımı Hızı Gecikmesine Uygula özelliğini ayarlamayı öğrenin ve Özellikler penceresi.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, test mix model
ms.assetid: ae8b35f9-d465-4d72-8d7d-7b56ae6ffd22
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: db93dbbfadc33c8653bd44e6343cfcea5bbc5f1c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122092559"
---
# <a name="how-to-apply-distribution-to-pacing-delay-for-a-user-pace-test-mix-model"></a>Nasıl yapılır: Kullanıcı hızı test karışımı modeli için adımlama gecikmesine dağıtım uygulama

Yük testini New Yük Testi Sihirbazı kullanarak **oluşturdukktan** sonra, senaryonun özelliklerini test Yük Testi Sihirbazı hedeflerinizi karşılayacak şekilde değiştirmek için Yük Testi Düzenleyicisi'ı kullanabilirsiniz.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Hızı **Geciktirme Özelliğine Dağıtım** Uygula özelliği Özellikler penceresi **kullanılarak** ayarlanır. Yük testi senaryosu özellikleri, Yük Testi Düzenleyicisi.

> [!NOTE]
> Hızı **Geciktirmek için Dağıtımı Uygula** özelliği yalnızca yük testi *karışımı* kullanıcı hızına göre yapılandırılmışsa geçerlidir. Daha fazla bilgi için, [test çalıştıran bir sanal kullanıcının olasılığını belirtmek için bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

Dağıtımı Gecikme **Süresine Uygula değeri** true veya false olarak ayarlanmış olabilir:

- **Doğru:** Senaryo, Test Karışımını Düzenle iletişim kutusundaki Kullanıcı  Başına Testler sütunundaki değer tarafından belirtilen normal istatistiksel dağıtım **gecikmelerini** uygular. Daha fazla bilgi için, [test çalıştıran bir sanal kullanıcının olasılığını belirtmek için bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

     Örneğin, test karışımını düzenle **iletişim** kutusunda Test  Karışımını Düzenle iletişim kutusunda Saat Başına Kullanıcı Başına Testler değerinin saat başına iki kullanıcı olarak ayar olduğunu varsayalım. Hızı **Geciktirme özelliğine Dağıtımı** Uygula özelliği **True** olarak ayarlanırsa, testler arasındaki bekleme süresine normal bir istatistiksel dağılım uygulanır. Testler saatte iki test çalıştırmaya devam ediyor ancak aralarında 30 dakikalık gecikme olması şart değildir. İlk test dört dakika sonra, ikinci test ise 45 dakika sonra çalışmasına neden olabilir.

- **Yanlış:** Testler, Test Karışımını Düzenle iletişim kutusundaki  Kullanıcı Başına Test Sayısı sütunundaki değer için belirttiğiniz **hızda** çalışıyor. Daha fazla bilgi için, [test çalıştıran bir sanal kullanıcının olasılığını belirtmek için bkz. Metin karışımı modellerini düzenleme.](../test/edit-test-mix-models-to-specify-the-probability-of-a-virtual-user-running-a-test.md)

     Örneğin, test karışımını düzenle **iletişim** kutusunda Test  Karışımını Düzenle iletişim kutusunda Saat Başına Kullanıcı Başına Testler değerinin saat başına iki kullanıcı olarak ayar olduğunu varsayalım. Pacing **Delay'e Dağıtımı** Uygula özelliği **False** olarak ayarlanırsa, testlerinizi çalıştıracaksanız hiçbir izin vermiyorsanız. Test 30 dakikada bir ecek. Bu, saatte iki test yürütmeyi sağlar.

## <a name="to-specify-the-apply-distribution-to-pacing-delay-property-setting-for-a-scenario"></a>Bir senaryo için Hızı Geciktirmek için Dağıtımı Uygula özellik ayarını belirtmek için

1. Yük testi açın.

   Yük Testi Düzenleyicisi  görüntülenir. Yük testi ağacı görüntülenir.

2. Yük **testi ağacının** Senaryolar klasöründe, ilerleme dağıtımını uygulamak istediğiniz senaryo düğümünü seçin.

3. Görünüm menüsünde **Özellikler** **Penceresi'ne tıklayın.**

   Senaryonun kategorileri ve özellikleri Özellikler **penceresinde** görüntülenir.

4. Dağıtımı Hızı Gecikmesine Uygula **özelliğinin değerinde True** veya False **seçeneğini** **seçin.**

5. Dosya **Kaydet'i**  >  **seçin.** Artık yük testini yeni Hızı Geciktirme Dağıtımı **Uygula değeriyle** çalıştırabileceksiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük testi senaryolarını düzenleme](../test/edit-load-test-scenarios.md)
- [İzlenecek yol: Yük testi oluşturma ve çalıştırma](../test/walkthrough-create-and-run-a-load-test.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
- [Yük testi senaryosu özellikleri](../test/load-test-scenario-properties.md)
