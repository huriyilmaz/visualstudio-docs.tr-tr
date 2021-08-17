---
title: Test aracısı yapılandırma
description: Aracınızı bir hizmet yerine işlem olarak çalıştıracak şekilde ayarerek masaüstüyle etkileşimde bulunarak otomatikleştirilmiş testler çalıştırmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 09/18/2018
ms.topic: how-to
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.openlocfilehash: 238c266d11c1057ab59fe5296edc514cfdc2d937
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075846"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Nasıl yapılacak: Test aracınızı masaüstüyle etkileşimde bulunacak testleri çalıştıracak şekilde ayarlama

::: moniker range="vs-2017"
Masaüstüyle etkileşimde bulunarak otomatikleştirilmiş testler çalıştırmak için aracınızı bir hizmet yerine işlem olarak çalıştıracak şekilde ayarlayabilirsiniz. Örneğin, test denetleyicisi ve test aracısı kullanarak kodlanmış ui testini uzaktan çalıştırmak veya test çalıştırarak bir video kaydı yakalamak için aracınızı bir işlem olarak çalıştıracak şekilde ayarlamanız gerekir. Visual Studio kullanarak test ayarlarınıza aracı atadığınız veya Microsoft Test Yöneticisi kullanarak ortamınız içinde rollere aracı atadığınız zaman, masaüstüyle etkileşim kurması gereken rollere atanmış tüm aracıların kurulumunu değiştirebilirsiniz.
::: moniker-end
::: moniker range=">=vs-2019"
Masaüstüyle etkileşimde bulunarak otomatikleştirilmiş testler çalıştırmak için aracınızı bir hizmet yerine işlem olarak çalıştıracak şekilde ayarlayabilirsiniz. Örneğin, test denetleyicisi ve test aracısı kullanarak kodlanmış ui testini uzaktan çalıştırmak veya test çalıştırarak bir video kaydı yakalamak için aracınızı bir işlem olarak çalıştıracak şekilde ayarlamanız gerekir. Visual Studio kullanarak test ayarlarınıza rollere aracı atadığınız zaman, masaüstüyle etkileşim kurması gereken rollere atanmış tüm aracıların kurulumunu değiştirebilirsiniz.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Laboratuvar ortamı Microsoft Test Yöneticisi için bu aracıyı kullanırsanız, test aracısı yüklenir. Ortam Oluşturma **Sihirbazı'nda kodlanmış** UI testlerini çalıştırmak için rollerden birini yapılandırmak istediğinizi belirtebilirsiniz.
:::moniker-end

> [!IMPORTANT]
> Üzerinde kodlanmış UI testleri çalıştırmak istediğiniz bir aracıyı çalıştıran bilgisayar kilit olamaz veya etkin ekran koruyucuya sahip olamaz.

Tarayıcıyı başlatan kodlanmış UI testleri çalıştırdısanız, bu tarayıcıyı başlatmak için test aracısına hizmet hesabı kullanılır. Bu hizmet hesabı, bu bilgisayarda etkin kullanıcı olan kullanıcı hesabıyla aynı olmalıdır. Aynı kullanıcı hesabı yoksa tarayıcı başlamaz.

> [!IMPORTANT]
> Derleme tanımının bir parçası olarak tarayıcıyı başlatan kodlanmış bir UI testi çalıştırdıysanız, bu tarayıcıyı başlatmak için derleme hizmetinin hizmet hesabı kullanılır. Bu hizmet hesabı, bu bilgisayarda etkin kullanıcı olan kullanıcı hesabıyla aynı olmalıdır. Aynı kullanıcı hesabı yoksa tarayıcı başlamaz.

Masaüstüyle etkileşim kurması gereken bir görevi gerçekleştiren bir role atanmış aracıları ayarlamak için aşağıdaki yordamı kullanın.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>Aracıyı işlem olarak çalıştıracak şekilde ayarlamak için

1. Bir işlem olarak çalıştırmak üzere yüklemiş olduğunu test aracıyı yapılandırmak için Test Aracısı Yapılandırma **Aracını**  >  **Başlat'a gidin.**

   Test **Aracılarını Yapılandır** iletişim kutusu görüntülenir.

   ![Test Aracısı'Visual Studio](media/configure-test-agent.png)

2. Etkileşimli **İşlem'i seçin.** Test aracısı bir hizmet yerine bir işlem olarak başlatacak. **İleri**’yi seçin.

3. Test aracısı işlemini çalıştıracak kullanıcının kullanıcı adını ve parolasını girin.

   > [!NOTE]
   > - Işlemi başlatmak için ekleyceğe ekleyseniz, bu aracı için test denetleyicisi için bilgisayarda TeamTestAgentService grubunun bir üyesi olarak da eklenmiştir. Bu kullanıcı geçerli kullanıcı ise, bu kullanıcı test denetleyicisi bilgisayarına eklerken oturumu kapatmanız veya yeniden başlatmanız gerekir.
   > - Kullanıcı hesapları için null parolalar desteklenmiyor.
   > - IntelliTrace'i veya ağ öykünme verilerini ve tanılama bağdaştırıcısını kullanmak için kullanıcı hesabının Yöneticiler grubunun bir üyesi olması gerekir. Test aracısı çalıştıran makine, Kullanıcı Hesabı'Least-Privileged işletim sistemi çalıştırıyorsa, bunu yönetici olarak da çalıştırmanız (yükseltilmiş) gerekir. Aracı kullanıcı adı aracı hizmetinde yoksa, test denetleyicisinde izinler gerektiren aracıyı eklemeye dener.
   > - Test denetleyicisini kullanmaya çalışan kullanıcının test denetleyicisinin Kullanıcılar hesabında olması gerekir, yoksa denetleyiciye karşı testleri çalıştıramayabilecektir.

4. Yeniden başlatma sonrasında test aracısı olan bir bilgisayarın testleri çalıştırana kadar bilgisayarı otomatik olarak test aracısı kullanıcısı olarak oturum açması için ayarlayabilirsiniz. Otomatik olarak **oturum aç'ı seçin.** Bu, kullanıcı adını ve parolayı kayıt defterinde şifrelenmiş bir biçimde depolar.

   > [!NOTE]
   > Laboratuvar ortamına uzak masaüstü veya konuk tabanlı bir bağlantı kullanarak bağlandıktan sonra sık sık, beklenmeyen bağlantı kesintileri yaşanabilirsiniz. Bağlantı kaybının olası nedenlerinden biri, makinenin otomatik olarak ağ üzerinde oturum açmak üzere yapılandırılmasıdır.

5. Ekran koruyucunun devre dışı bırakıldı olduğundan emin olmak için masaüstüyle etkileşim kurması gereken tüm otomatikleştirilmiş testleri etkileyene kadar ekran koruyucunun devre dışı **bırakıldı olduğundan emin olun.**

   > [!WARNING]
   > Otomatik olarak oturum asanız veya ekran koruyucusunu devre dışı bırakırsanız güvenlik riskleri vardır. Otomatik oturum açma özelliğini etkinleştirerek, diğer kullanıcıların bu bilgisayarı başlatmalarını ve otomatik olarak oturum açtığı hesabı kullanamalarını sağlarsınız. Ekran koruyucusunu devre dışı bırakırsanız, bilgisayar bir kullanıcının bilgisayarın kilidini açmak için oturum açmasını isteminde çalışmayabilir. Bu, bilgisayara fiziksel erişimi olan herkesin bilgisayara erişmelerini sağlar. Bu özellikleri bir bilgisayarda etkinleştirirsanız, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olun. Örneğin, bu bilgisayarlar fiziksel olarak güvenli bir laboratuvarda bulunur. Ekran koruyucunun **devre dışı bırakıldı olduğundan emin olmak** ayarını temizlersanız bu, ekran koruyucusunu etkinleştirmez.

   Aracıyı hizmet olarak çalıştıracak şekilde geri değiştirmek için bu aracıyı kullanabilir ve Hizmet'i **seçin.**

6. Değişikliklerinizi uygulamak için Uygulama'ya **Ayarlar.**

   Test **aracınızı** yapılandırma adımlarının her birini gösteren bir Yapılandırma özeti iletişim kutusu görüntülenir.

7. Yapılandırma özeti iletişim **kutusunu kapatmak** için Kapat'ı **seçin.** Ardından Yeniden **Kapat'ı** seçen **Test Aracısı Yapılandırma Aracı'nı kapatın.**

   > [!NOTE]
   > İşlem olarak çalışan bir test aracısı için bilgisayarda çalışan bir bildirim alanı simgesi vardır. Test aracılarının durumunu gösterir. Bu aracıyı kullanarak bir işlem olarak çalıştırılacaksa aracıyı başlatabilirsiniz, durdurabilir veya yeniden başlatabilirsiniz. Test aracısı çalışmıyorsa işlem olarak başlatmak için Test Aracısı'Visual Studio  >    >  **Microsoft Visual Studio seçin.**

   ::: moniker range="vs-2017"
   Bu test aracısı için test denetleyicisi Team Foundation Server ile kaydedilmişse, etkileşimli bir işlem olarak çalışan bir test  aracısını durumu, Microsoft Test Yöneticisi için **Laboratuvar** Merkezi'nde denetleyiciler görünümünde görüntülenir. Etkileşimli bir işlem olarak çalıştırlı olduğunu ifade etmek için yukarıdaki yıldız simgesiyle listelenir. Bu test aracıyı yeniden başlatmak için, Denetleyiciler görünümü için değil, test aracısı için bilgisayarda çalışan aracıyı **kullansanız gerekir.**
   ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
