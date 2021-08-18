---
title: 'Nasıl yapılır: Yük Testi Sonuçları Deposunu Seçme'
description: Test sonuçlarınızı depolamak için yerel veya uzak SQL sunucusu tanımlamayı öğrenin. Sunucunun bir yük testi sonuçları deposu olması gerekir.
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
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 9e0177154cec399a509046679f7336097873fbc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075872"
---
# <a name="how-to-select-a-load-test-results-repository"></a>Nasıl: Yük testi sonuçları deposu seçme

Yerel sonuçlar deposuyla sınırlı değildir. Yük testleri genellikle uzak bir Aracı bilgisayar kümesi üzerinde çalışır. Aracılar, bir denetleyiciyle birlikte, tek bir bilgisayardan daha fazla sanal yük üretebilirsiniz. Daha fazla bilgi için [bkz. Test denetleyicileri ve test aracıları.](configure-test-agents-and-controllers-for-load-tests.md)

Aracılar veya yerel bilgisayarınızdan alınan test sonuçları, yük testi SQL oluşturduğunuz herhangi bir sunucuya kaydedilebilir. Her iki durumda da, Test Denetleyicilerini Yönet penceresini kullanarak yük testi sonuçlarınızı depolamak **istediğiniz yeri tanımlamanız** gerekir.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="identify-a-results-store-for-load-test-data"></a>Yük testi verileri için bir sonuç deposu tanımlama

1. Bu **Çözüm Gezgini** yük testi dosyanızı açın.

2. Yük Testi **araç çubuğundan Test** Denetleyicilerini **Yönet'i seçin.** **Test Denetleyicisini Yönet** iletişim kutusu görüntülenir. Uzaktan bir aracı kullanıyorsanız, bir denetleyici seçmeniz gerekir.

     ![Yük testi sonuçları depolama bağlantı özellikleri ](../test/media/loadtestconnectionproperties.png) Test sonuçları deposu bağlantı özellikleri

3. Test **sonuçlarını yükle depolamada Bağlantı** Özellikleri iletişim kutusunu görüntülemek için **(...)** **seçeneğine** tıklayın.

4. Sunucu **Adı'nın** altında, betikleri çalıştırarak sunucunun adını `LoadTest` yazın.

    > [!TIP]
    > Yük testi deposu için yerel makinenize SQL Express kullanıyorsanız \<computername> \sqlexpress (örneğin, **MyComputer\sqlexpress) girin.**

5. Sunucuda **oturum aç altında, Kimlik Doğrulaması** için **Kullan'Windows seçebilirsiniz.** Kullanıcı adını ve parolayı belirtebilirsiniz, ancak bunu yaptıysanız Parolamı kaydet **seçeneğini belirtmeniz gerekir.**

6. Veritabanına **Bağlan altında Veritabanı** adı seçin veya **girin'i seçin.** Açılan **liste kutusundan LoadTest'i** seçin.

7. **Tamam'ı seçin.** Bağlantıyı Test Edin'i seçerek **bağlantıyı test edin.**

8. Test **Denetleyicisini** Yönet **iletişim kutusunda Kapat'ı** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Load Test Sonuçları Repository'de yük testi sonuçlarını yönetme](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Test denetleyicileri ve test aracıları](configure-test-agents-and-controllers-for-load-tests.md)
