---
title: 'Nasıl yapılır: Yük Testi Sonuçları Deposunu Seçme'
description: Test sonuçlarınızı depolamak için yerel veya uzak bir SQL Server 'ı nasıl tanımlayacağınızı öğrenin. Sunucu bir yük testi sonuçları deposuna sahip olmalıdır.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
f1_keywords:
- vs.test.load.dialog.connectstringmissing
- vs.test.load.dialog.databaseconnectstring
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
- SQL, Load Test Results Store
ms.assetid: fa0c4dd9-612f-4a57-b8eb-458f129d9cda
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ada73cc1f907a298a2cc1efcf3281fb8a219ef32
ms.sourcegitcommit: 02f14db142dce68d084dcb0a19ca41a16f5bccff
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2020
ms.locfileid: "95439946"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Nasıl yapılır: yük testi sonuçları deposu seçme

Yerel bir sonuç deposuyla sınırlı değilsiniz. Genellikle, yük testleri, uzak bir aracı bilgisayarları kümesi üzerinde çalıştırılır. Aracılar, bir denetleyici ile birlikte, tek bir bilgisayardan daha fazla benzetimli yük oluşturabilir. Daha fazla bilgi için bkz. [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md).

Aracılarınızdan veya yerel bilgisayarınızda test sonuçları, yük testi sonuçları deposu oluşturduğunuz herhangi bir SQL Server 'a kaydedilebilir. Her iki durumda da, **Test Denetleyicilerini Yönet** penceresini kullanarak yük testi sonuçlarınızı nerede depolamak istediğinizi belirlemeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Yük testi verileri için bir sonuç deposu tanımla

1. **Çözüm Gezgini**' de, yük testi dosyanızı açın.

2. **Yük testi** araç çubuğundan, **Test Denetleyicilerini Yönet**' i seçin. **Test denetleyicisini Yönet** iletişim kutusu görüntülenir. Uzaktan aracı kullanıyorsanız, bir denetleyici seçmelisiniz.

     ![Yük testi sonuçları deposu bağlantı özellikleri ](../test/media/loadtestconnectionproperties.png) Yük testi sonuçları deposu bağlantı özellikleri

3. **Yük testi sonuçları deposunda**, **bağlantı özellikleri** iletişim kutusunu göstermek için **(...)** seçeneğine tıklayın.

4. **Sunucu adı**' nda, betikleri çalıştırdığınız sunucunun adını yazın `LoadTest` .

    > [!TIP]
    > Yük testi deposu için yerel makinenizde SQL Express kullanıyorsanız, \<computername> \SQLEXPRESS (örneğin, **mymakinesqlexpress**) yazın.

5. **Sunucuda oturum** aç ' ın altında, **Windows kimlik doğrulamasını kullan**' ı seçebilirsiniz. Kullanıcı adını ve parolayı belirtebilirsiniz, ancak bunu yaparsanız **Parolamı kaydet** seçeneğini belirlemeniz gerekir.

6. **Veritabanına Bağlan**' ın altında, Seç ' i **veya bir veritabanı adı girin**' i seçin. Açılan liste kutusundan **LoadTest** öğesini seçin.

7. **Tamam ' ı** seçin. Bağlantıyı **Sına**' yı seçerek bağlantıyı test edebilirsiniz.

8. **Test denetleyicisini Yönet** Iletişim kutusunda **Kapat** ' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük Test Sonuçları deposundaki yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
