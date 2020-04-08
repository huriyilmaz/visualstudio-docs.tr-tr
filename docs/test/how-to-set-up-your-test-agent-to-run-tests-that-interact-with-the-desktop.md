---
title: Test aracını yapılandırma
ms.date: 09/18/2018
ms.topic: conceptual
helpviewer_keywords:
- agents, configuring for interaction with desktop
ms.assetid: 3a94dd07-6d17-402c-ae8f-7947143755c9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dc00598595ee3e3d958562682900bde9aad2a353
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880188"
---
# <a name="how-to-set-up-your-test-agent-to-run-tests-that-interact-with-the-desktop"></a>Nasıl kullanılır: Test aracınızı masaüstüyle etkileşimde olan testleri çalıştıracak şekilde ayarlama

::: moniker range="vs-2017"
Masaüstüyle etkileşimde olan otomatik testler çalıştırmak istiyorsanız, aracınızı hizmet yerine bir işlem olarak çalışacak şekilde ayarlamanız gerekir. Örneğin, bir test denetleyicisi ve test aracısı kullanarak uzaktan kodlanmış bir UI testi çalıştırmak istiyorsanız veya bir test çalıştırmak ve çalıştırdığınızda bir video kaydı yakalamak istiyorsanız, aracınızı bir işlem olarak çalışacak şekilde ayarlamanız gerekir. Visual Studio'yu kullanarak test ayarlarınızdaki rollere aracılar atadığınızda veya Microsoft Test Yöneticisi'ni kullanarak ortamınızdaki rollere aracılar atadığınızda, masaüstüyle etkileşimde olması gereken rollere atanan tüm aracıların kurulumunu değiştirmeniz gerekir.
::: moniker-end
::: moniker range=">=vs-2019"
Masaüstüyle etkileşimde olan otomatik testler çalıştırmak istiyorsanız, aracınızı hizmet yerine bir işlem olarak çalışacak şekilde ayarlamanız gerekir. Örneğin, bir test denetleyicisi ve test aracısı kullanarak uzaktan kodlanmış bir UI testi çalıştırmak istiyorsanız veya bir test çalıştırmak ve çalıştırdığınızda bir video kaydı yakalamak istiyorsanız, aracınızı bir işlem olarak çalışacak şekilde ayarlamanız gerekir. Visual Studio'yu kullanarak test ayarlarınızdaki rollere aracılar atadığınızda, masaüstüyle etkileşimde olması gereken rollere atanan aracıların kurulumunu değiştirmeniz gerekir.
::: moniker-end

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

::: moniker range="vs-2017"
> [!WARNING]
> Bir laboratuvar ortamı ayarlamak için Microsoft Test Yöneticisi'ni kullanıyorsanız, test aracısını yükler. Kodlanmış Kullanıcı Bulma Birimi testlerini çalıştırmak için rollerden birini yapılandırmak **istediğinizi Ortam Oluşturma** Sihirbazı'nda belirtebilirsiniz.
:::moniker-end

> [!IMPORTANT]
> Kodlu UI testlerini çalıştırmak istediğiniz bir aracıyı çalıştıran bilgisayar kilitlenemez veya etkin bir ekran koruyucuya sahip olamaz.

Bir tarayıcıyı başlatan kodlanmış UI testlerini çalıştırıyorsanız, test aracısının hizmet hesabı bu tarayıcıyı başlatmak için kullanılır. Bu hizmet hesabı, bu bilgisayardaki etkin kullanıcı olan kullanıcı hesabıyla aynı olmalıdır. Aynı kullanıcı hesabı değilse, tarayıcı başlamaz.

> [!IMPORTANT]
> Yapı tanımının bir parçası olarak tarayıcıyı başlatan kodlanmış bir UI testi çalıştırıyorsanız, yapı hizmetinin hizmet hesabı bu tarayıcıyı başlatmak için kullanılır. Bu hizmet hesabı, bu bilgisayardaki etkin kullanıcı olan kullanıcı hesabıyla aynı olmalıdır. Aynı kullanıcı hesabı değilse, tarayıcı başlamaz.

Masaüstüyle etkileşimde olması gereken bir görevi gerçekleştiren bir role atanan aracıları ayarlamak için aşağıdaki yordamı kullanın.

## <a name="to-set-up-an-agent-to-run-as-a-process"></a>İşlem olarak çalışacak bir aracı ayarlamak için

1. İşlem olarak çalıştırmak için yüklediğiniz test aracısını yapılandırmak için **Test** > **Aracısını Çalıştırma Yapılandırma Aracı'na**gidin.

   **Yapılaşı Test Aracısı** iletişim kutusu görüntülenir.

   ![Visual Studio için Test Aracısı Yapılandır](media/configure-test-agent.png)

2. **Etkileşimli İşlem'i**seçin. Test aracısı bir hizmet yerine bir işlem olarak başlatılacaktır. **İleri**’yi seçin.

3. Test aracısı işlemini çalıştıracak kullanıcının kullanıcı adını ve parolasını girin.

   > [!NOTE]
   > - İşlemi başlatmak için eklediğiniz kullanıcı, bu aracının test denetleyicisi için bilgisayardaki TeamTestAgentService grubunun bir üyesi olarak da eklenmelidir. Bu kullanıcı geçerli kullanıcıysa, bu kullanıcıyı test denetleyicisi bilgisayarına eklediğinizde oturumu kapatmanız veya yeniden başlatmanız gerekir.
   > - Null parolalar kullanıcı hesapları için desteklenmez.
   > - IntelliTrace veya ağ öykünme verilerini ve tanıadaptörü kullanmak istiyorsanız, kullanıcı hesabı Yöneticiler grubunun bir üyesi olmalıdır. Test aracısını çalıştıran makine En Az Ayrıcalıklı Kullanıcı Hesabı olan bir işletim sistemi çalıştırıyorsa, bunu yönetici olarak da çalıştırmanız gerekir (yükseltilmiş). Aracı kullanıcı adı aracı hizmetinde değilse, test denetleyicisinde izingerektiren eklemeye çalışır.
   > - Test denetleyicisini kullanmaya çalışan kullanıcı test denetleyicisinin Kullanıcılar hesabında olmalıdır veya testleri denetleyiciye karşı çalıştıramaz.

4. Test aracısı olan bir bilgisayarın yeniden başlatıldıktan sonra testleri çalıştırabilmesini sağlamak için, bilgisayarı test aracısı kullanıcısı olarak otomatik olarak oturum açacak şekilde ayarlayabilirsiniz. **Oturum Aç'ı otomatik olarak**seçin. Bu, kullanıcı adı ve parolayı kayıt defterinde şifreli bir biçimde saklar.

   > [!NOTE]
   > Uzak bir masaüstü veya konuk tabanlı bir bağlantı kullanarak laboratuvar ortamına bağlandığınızda, sık sık beklenmeyen kopukluklar yaşayabilirsiniz. Bağlantı kaybının olası bir nedeni, makinenin ağa otomatik olarak oturum açacak şekilde yapılandırılmış olmasıdır.

5. Bu, masaüstüyle etkileşimde olması gereken otomatik testleri etkileyebileceğinden ekran koruyucunun devre dışı bırakıldığından emin olmak için **ekran koruyucunun devre dışı bırakıldığından emin olun'u**seçin.

   > [!WARNING]
   > Otomatik olarak oturum açarsanız veya ekran koruyucuyu devre dışı btanırsanız güvenlik riskleri vardır. Otomatik oturum açmayı etkinleştirerek, diğer kullanıcıların bu bilgisayarı başlatmasını ve otomatik olarak oturum açan hesabı kullanabilmesini sağlarsınız. Ekran koruyucuyu devre dışı bederseniz, bilgisayar bir kullanıcının bilgisayarın kilidini açmak için oturum açmasını istemeyebilir. Bu, bilgisayarın fiziksel erişimi olan herkesin bilgisayara erişmesini sağlar. Bu özellikleri bilgisayarda etkinleştiriseniz, bu bilgisayarların fiziksel olarak güvenli olduğundan emin olmalısınız. Örneğin, bu bilgisayarlar fiziksel olarak güvenli bir laboratuarda bulunur. **Ekran koruyucunun devre dışı bırakıldığından emin**olun'u temizlerseniz, bu ekran koruyucunuza izin vermez.

   Aracıyı hizmet olarak çalışacak şekilde değiştirmek için bu aracı kullanabilir ve **Hizmet'i**seçebilirsiniz.

6. Değişikliklerinizi uygulamak için **Ayarlar'ı Uygula'yı**seçin.

   Test aracınızı yapılandırmak için her adımın durumunu gösteren bir **Yapılandırma özeti** iletişim kutusu görüntülenir.

7. **Yapılandırma özeti** iletişim kutusunu kapatmak için **Kapat'ı**seçin. Ardından **Test Aracısı Yapılandırma Aracısını**kapatmak için yeniden **kapat'ı** seçin.

   > [!NOTE]
   > İşlem olarak çalışan bir test aracısı için bilgisayarda çalışan bir bildirim alanı simgesi vardır. Test aracısının durumunu gösterir. Bu aracı kullanarak bir işlem olarak çalışıyorsa aracıyı başlatabilir, durdurabilir veya yeniden başlatabilirsiniz. Test aracısını çalışmıyorsa bir işlem olarak başlatmak için Görsel **Stüdyo'yu Başlat** > Microsoft Visual**Studio** > **Test Aracısı'nı**seçin.

   ::: moniker range="vs-2017"
   Bu test aracısının test denetleyicisi Team Foundation Server'a kayıtlıysa, etkileşimli işlem olarak çalışan bir test aracısının durumu Microsoft Test Yöneticisi Için **Laboratuvar Merkezi'ndeki** **Denetleyiciler** görünümünde görüntülenir. Etkileşimli bir işlem olarak çalıştığını belirtmek için önceki bir yıldız işareti yle listelenir. Bu test aracısını yeniden başlatmak için, **Denetleyiciler** görünümü için değil, test aracısı için bilgisayarda çalışan aracı kullanmanız gerekir.
   ::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.

- [Test aracılarını yükleme ve yapılandırma](../test/lab-management/install-configure-test-agents.md)
