---
title: 'Nasıl yapılır: Yük Testi Sonuçları Deposunu Seçme'
ms.date: 10/19/2016
ms.topic: conceptual
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
ms.openlocfilehash: 513dd884f65e041e7ad90dda1483633fec57e100
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589012"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Nasıl seçilir: Yük testi sonuçları deposunu seçin

Yerel bir sonuç deposuyla sınırlı değildir. Sık sık, yükleme testleri Aracılı bilgisayarların uzak bir kümesi nde çalıştırılır. Aracılar, bir denetleyici ile birlikte, herhangi bir bilgisayardan daha fazla simüle yük oluşturabilir. Daha fazla bilgi için test [denetleyicileri ve test aracıları'na](configure-test-agents-and-controllers-for-load-tests.md)bakın.

Aracılarınızın veya yerel bilgisayarınızın test sonuçları, bir yük testi sonuçları deposu oluşturduğunuz herhangi bir SQL sunucusuna kaydedilebilir. Her iki durumda da, **Test Denetleyicilerini Yönet** penceresini kullanarak yük testi sonuçlarınızı nerede saklamak istediğinizi belirlemeniz gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Yük testi verileri için bir sonuç deposu belirleme

1. **Solution Explorer'da**yük testi dosyanızı açın.

2. Yük **Testi** araç çubuğundan, **Test Denetleyicilerini Yönet'i**seçin. **Test Denetleyicisini Yönet** iletişim kutusu görüntülenir. Aracıyı uzaktan kullanıyorsanız, bir denetleyici seçmeniz gerekir.

     ![Yük test sonuçları](../test/media/loadtestconnectionproperties.png) mağaza bağlantı özellikleri Yük test sonuçları mağaza bağlantı özellikleri

3. Yükle **test sonuçları deposunda**Bağlantı **Özellikleri** iletişim kutusunu görüntülemek için **(...)** seçeneğini tıklatın.

4. **Sunucu Adı'nda,** `LoadTest` komut dosyalarını çalıştırdığınız sunucunun adını yazın.

    > [!TIP]
    > Yükleme testi deposu için yerel makinenizde SQL Express \<kullanıyorsanız, bilgisayar adı>\sqlexpress (örneğin, **MyComputer\sqlexpress)** girin.

5. **Sunucuda Oturum Aç**altında, **Windows Kimlik Doğrulaması kullan'ı**seçebilirsiniz. Kullanıcı adı ve şifrenizi belirtebilirsiniz, ancak bunu **yaparsanız, şifremi kaydet**seçeneğini seçmeniz gerekir.

6. **Veritabanına Bağlan'ın**altında, **Bir veritabanı adı seçin veya bir veritabanı adı girin.** Açılan liste kutusundan **LoadTest'i** seçin.

7. **Tamam'ı**seçin. **Test Bağlantısı'nı**seçerek bağlantıyı test edebilirsiniz.

8. **Test Denetleyicisini Yönet** iletişim kutusunda **Kapat'ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Yük Testi Sonuçları Deposu'nda yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
