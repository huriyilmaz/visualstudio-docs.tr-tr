---
title: Azure araçlarını kullanarak bir bulut hizmeti yayımlama | Microsoft Docs
description: Visual Studio kullanarak Azure Cloud Service projelerini yayımlama hakkında bilgi edinin.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: cd41925fb1b9078b108213870b95d328c81103a0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122114452"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Visual Studio kullanarak bulut hizmetini yayımlama

Visual Studio, bir uygulamayı bir bulut hizmetinin hem hazırlık hem de üretim ortamları için desteğiyle doğrudan Azure 'da yayımlayabilirsiniz. Yayımlarken, dağıtım paketini ve dağıtım paketi için geçici olarak kullanılan bir depolama hesabını seçersiniz.

Bir Azure uygulaması geliştirirken ve sınadığınızda, değişiklikleri Web rolleriniz için artımlı olarak yayımlamak üzere Web Dağıtımı kullanabilirsiniz. Uygulamanızı bir dağıtım ortamında yayımladıktan sonra, Web Dağıtımı değişiklikleri doğrudan Web rolünü çalıştıran sanal makineye dağıtmanızı sağlar. Değişiklikleri test etmek için Web rolünüzü güncelleştirmek istediğiniz her seferinde tüm Azure uygulamanızı paketleyip yayımlamanız gerekmez. Bu yaklaşımla, uygulamanızın bir dağıtım ortamında yayımlanmasını beklemeden, test için Web rolünüzün değişikliklerinizin bulutta kullanılabilmesini sağlayabilirsiniz.

Azure uygulamanızı yayımlamak ve Web Dağıtımı kullanarak bir Web rolünü güncelleştirmek için aşağıdaki yordamları kullanın:

- Visual Studio bir Azure uygulaması yayımlama veya paketleme
- Geliştirme ve test döngüsünün bir parçası olarak bir Web rolünü güncelleştirme

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Visual Studio bir Azure uygulaması yayımlama veya paketleme

Azure uygulamanızı yayımladığınızda, aşağıdaki görevlerden birini yapabilirsiniz:

- Bir hizmet paketi oluşturun: uygulamanızı [Azure Portal](https://portal.azure.com)bir dağıtım ortamında yayımlamak için bu paketi ve hizmet yapılandırma dosyasını kullanabilirsiniz.

- azure projenizi Visual Studio yayımlama: uygulamanızı doğrudan Azure 'da yayımlamak için, yayımlama sihirbazı 'nı kullanın. Bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Visual Studio bir hizmet paketi oluşturmak için

1. Uygulamanızı yayımlamaya hazırsanız Çözüm Gezgini açın, rollerinizi içeren Azure projesi için kısayol menüsünü açın ve Yayımla ' yı seçin.

1. Yalnızca bir hizmet paketi oluşturmak için aşağıdaki adımları izleyin:

   a. Azure projesinin kısayol menüsünde **paket**' i seçin.

   b. **Paket Azure uygulaması** iletişim kutusunda, paket oluşturmak istediğiniz hizmet yapılandırmasını seçin ve ardından yapı yapılandırmasını seçin.

   c. Seçim yayımladıktan sonra bulut hizmeti için uzak masaüstü 'nü açmak üzere **tüm roller için uzak masaüstünü etkinleştir**' i seçin ve ardından uzak masaüstü kimlik bilgilerini yapılandırmak için **Ayarlar** ' ı seçin. Daha fazla bilgi için bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Yayımladıktan sonra bulut hizmetinizde hata ayıklamak istiyorsanız, uzaktan hata ayıklamayı **tüm roller Için etkinleştir**' i seçerek açın.

   d. Paketi oluşturmak için **paket** bağlantısını seçin.

      Dosya Gezgini, yeni oluşturulan paketin dosya konumunu gösterir. Bu konumu, Azure portal kullanabilmek için kopyalayabilirsiniz.

   e. Bu paketi bir dağıtım ortamında yayımlamak için, bir bulut hizmeti oluştururken ve bu paketi Azure portal bir ortama dağıttığınızda paket konumu olarak bu konumu kullanmanız gerekir.

1. Seçim Dağıtım işlemini iptal etmek için, etkinlik günlüğündeki satır öğesi için kısayol menüsünde **iptal ve Kaldır**' ı seçin. Bu komut dağıtım sürecini durduruyor ve dağıtım ortamını Azure 'dan siler. Dağıtımı tamamladıktan sonra ortamı kaldırmak için Azure portal kullanın.

1. Seçim rol örneklerinizin başlatılmasından sonra Visual Studio, dağıtım ortamını Sunucu Gezgini **Cloud Services** düğümünde otomatik olarak gösterir. Buradan, tek tek rol örneklerinin durumunu görebilirsiniz. Bkz. [bulut Gezgini Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md). Aşağıdaki çizimde, hala başlatma durumunda olan rol örnekleri gösterilmektedir:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Geliştirme ve test döngüsünün bir parçası olarak bir Web rolünü güncelleştirme

Uygulamanızın arka uç altyapısı kararlı ise, ancak Web rollerinin daha sık güncelleştirilmesi gerekiyorsa, projenizdeki yalnızca bir Web rolünü güncelleştirmek için Web Dağıtımı kullanabilirsiniz. Web Dağıtımı, arka uç çalışan rollerini yeniden oluşturmak ve yeniden dağıtmak istemediğinizde veya birden fazla Web rolüne sahipseniz ve yalnızca bir web rolünden yalnızca birini güncellemek istediğinizde yararlı olur.

### <a name="requirements-for-using-web-deploy"></a>Web Dağıtımı kullanma gereksinimleri

- **Yalnızca geliştirme ve test amaçlıdır**: değişiklikler doğrudan Web rolünün çalıştığı sanal makineye yapılır. Bu sanal makinenin geri dönüştürülmesi gerekiyorsa, değişiklikler kaybedilir çünkü yayımladığınız özgün paket, rol için sanal makineyi yeniden oluşturmak için kullanılır. Web rolü için en son değişiklikleri almak üzere uygulamanızı yeniden yayımlayın.

- **Yalnızca Web rolleri güncelleştirilemiyor**: çalışan rolleri güncelleştirilemiyor. Ayrıca, içinde ' yi güncelleştiremezsiniz `RoleEntryPoint` `web role.cs` .

- **Bir Web rolünün yalnızca tek bir örneğini destekleyebilir**: dağıtım ortamınızda herhangi bir Web rolünün birden çok örneği olamaz. Ancak, her biri yalnızca bir örneğe sahip birden çok web rolü desteklenir.

- **uzak masaüstü bağlantılarını etkinleştir**: bu gereksinim, Web Dağıtımı Internet Information Services (ııs) çalıştıran sunucuya değişiklikleri dağıtmak üzere sanal makineye bağlanmak için kullanıcı ve parolayı kullanmasına izin verir. Ayrıca, bu sanal makinede IIS 'ye güvenilir bir sertifika eklemek için sanal makineye bağlanmanız gerekebilir. (Bu sertifika, Web Dağıtımı tarafından kullanılan IIS için Uzak bağlantının güvende olmasını sağlar.)

Aşağıdaki yordamda, **Azure uygulama yayımlama** Sihirbazı 'nı kullandığınız varsayılır.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Uygulamanızı yayımladığınızda Web Dağıtımı etkinleştirme

1. **Tüm Web rolleri için Web dağıtımı etkinleştir** seçeneğini etkinleştirmek için öncelikle Uzak Masaüstü bağlantıları 'nı yapılandırmanız gerekir. Tüm roller için **uzak masaüstünü etkinleştir** ' i seçin ve görüntülenen **Uzak Masaüstü yapılandırması** kutusuna uzaktan bağlanmak için kullanılan kimlik bilgilerini sağlayın. Bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Uygulamanızdaki tüm Web rolleri için Web Dağıtımı etkinleştirmek üzere **tüm Web rolleri için Web dağıtımı etkinleştir**' i seçin.

    Sarı bir uyarı üçgeni belirir. Web Dağıtımı, varsayılan olarak güvenilir olmayan, otomatik olarak imzalanan bir sertifika kullanır ve bu, hassas verileri karşıya yüklemek için önerilmez. Bu işlemi hassas veriler için güvenli hale getirmeniz gerekiyorsa Web Dağıtımı bağlantıları için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifikanın güvenilir bir sertifika olması gerekir. Daha fazla bilgi için bkz. [Web dağıtımı güvenli hale getirme](#make-web-deploy-secure).

1. **Özet** ekranını göstermek için **İleri** ' yi, sonra da bulut hizmetini dağıtmak için **Yayımla** ' yı seçin.

    Bulut hizmeti yayımlandı. Oluşturulan sanal makinede, Web rollerinizi yeniden yayımlamadan güncelleştirmek için Web Dağıtımı IIS için uzak bağlantılar etkinleştirilmiş olmalıdır.

   > [!NOTE]
   > Bir Web rolü için yapılandırılmış birden fazla örneğiniz varsa, her bir Web rolünün yalnızca uygulamanızı yayımlamak için oluşturulan pakette bir örnekle sınırlı olduğunu belirten bir uyarı iletisi görüntülenir. Devam etmek için **Tamam**'ı seçin. Gereksinimler bölümünde belirtildiği gibi, birden fazla Web rolüne sahip olabilirsiniz ancak her rolün yalnızca bir örneği olabilir.

### <a name="update-your-web-role-by-using-web-deploy"></a>Web rolünüzü Web Dağıtımı kullanarak güncelleştirin

1. Web Dağıtımı kullanmak için, yayımlamak istediğiniz Visual Studio Web rollerinizin herhangi biri için projede kod değişiklikleri yapın ve ardından çözümünüzde bu proje düğümüne sağ tıklayıp **yayımla**' yı işaret edin. **Web 'ı Yayımla** iletişim kutusu görüntülenir.

1. Seçim IIS için uzak bağlantılar için kullanmak üzere güvenilen bir SSL sertifikası eklediyseniz, **Güvenilmeyen sertifikaya Izin ver** onay kutusunu temizleyebilirsiniz. Web Dağıtımı güvenli hale getirmek için bir sertifika ekleme hakkında daha fazla bilgi için, bu makalede daha sonra **Web dağıtımı güvenli hale getirmek için** bölümüne bakın.

1. Web Dağıtımı kullanmak için, yayınlama mekanizmasına, paketi ilk yayımlandığında, uzak masaüstü bağlantınız için ayarladığınız Kullanıcı adı ve parola gerekir.

   a. **Kullanıcı adı** alanına kullanıcı adını girin.

   b. **Parola** alanına parolayı girin.

   c. Seçim Bu parolayı bu profilde kaydetmek istiyorsanız, **Parolayı kaydet**' i seçin.

1. Değişiklikleri Web rolünüzde yayımlamak için **Yayımla**' yı seçin.

    Durum satırı **Yayımlama başladı**' i görüntüler. Yayımlama tamamlandığında, **Yayımlama başarılı** görüntülenir. Değişiklikler artık sanal makinenizde Web rolüne dağıtıldı. Şimdi yaptığınız değişiklikleri test etmek için Azure uygulamanızı Azure ortamında başlatabilirsiniz.

### <a name="make-web-deploy-secure"></a>Web dağıtımı güvenli hale getirme

1. Web Dağıtımı, varsayılan olarak güvenilir olmayan, otomatik olarak imzalanan bir sertifika kullanır ve bu, hassas verileri karşıya yüklemek için önerilmez. Bu işlemi hassas veriler için güvenli hale getirmeniz gerekiyorsa Web Dağıtımı bağlantıları için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifikanın bir sertifika yetkilisinden (CA) edindiğiniz güvenilir bir sertifika olması gerekir.

    Web rollerinizin her biri için her bir sanal makine için Web Dağıtımı güvenli hale getirmek üzere, Web dağıtımı için kullanmak istediğiniz güvenilen sertifikayı Azure portal yüklemeniz gerekir. Bu sertifika, uygulamanızı yayımladığınızda web rolü için oluşturulan sanal makineye sertifikanın eklendiğinden emin olmanızı sağlar.

1. Uzaktan bağlantılar için kullanmak üzere IIS 'ye güvenilir bir SSL sertifikası eklemek için aşağıdaki adımları izleyin:

   a. web rolünü çalıştıran sanal makineye bağlanmak için, **Cloud Explorer** veya **Sunucu Gezgini** web rolü örneğini seçin ve ardından **uzak masaüstü komutunu kullanarak Bağlan** seçin. Sanal makineye bağlanma hakkında ayrıntılı adımlar için, bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Tarayıcınız bir dosya indirmenizi ister `.rdp` .

   b. SSL sertifikası eklemek için IIS Yöneticisi'nde yönetim hizmetini açın. IIS Yöneticisi'nde, Eylem bölmesinde **Bağlamalar bağlantısını açarak** **SSL'yi** etkinleştirin. Site **Bağlaması Ekle** iletişim kutusu görüntülenir. **Ekle'yi** ve ardından Tür **açılan** listesinde HTTPS'yi seçin. SSL **sertifikası listesinde,** bir CA tarafından imzalayan ve sertifika yetkilisine yüklediğiniz SSL sertifikasını Azure portal. Daha fazla bilgi için, [bkz. Configure Connection Ayarlar for the Management Service](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc770458(v=ws.10)).

      > [!NOTE]
      > Güvenilen bir SSL sertifikası eklersiniz, yayımla Sihirbazı'nda sarı uyarı **üçgeni artık görünür.**

## <a name="include-files-in-the-service-package"></a>Hizmet paketine dosya dahil etmek

Bir rol için oluşturulan sanal makinede kullanılabilir olacak şekilde hizmet paketinize belirli dosyaları dahil etmek zorundayabilirsiniz. Örneğin, hizmet paketinize başlangıç betiği tarafından kullanılan bir `.exe` veya dosyası eklemek istiyor `.msi` olabilir. Veya bir web rolü veya çalışan rolü projesinin gerektirdiği bir derleme eklemeniz de gerekli olabilir. Dosyaları dahil etmek için Azure uygulamanıza uygun çözüme ekleniyor olması gerekir.

1. Bir hizmet paketine derleme eklemek için aşağıdaki adımları kullanın:

   a. Bu **Çözüm Gezgini,** başvurulan derlemenin eksik olduğu projenin proje düğümünü açın.
   b. Derlemeyi projeye eklemek için Başvurular klasörünün kısayol menüsünü açın **ve Başvuru** Ekle'yi **seçin.** Başvuru Ekle iletişim kutusu görüntülenir.
   c. Eklemek istediğiniz başvuruya tıklayın ve ardından Tamam'ı **seçin.** Başvuru, Başvurular klasörünün altındaki **listeye** eklenir.
   d. Ekley istediğiniz derlemenin kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler **penceresi** görüntülenir.

      Bu derlemeyi hizmet paketine dahil etmek için, Yereli **Kopyala listesinde True'yi** **seçin.**
1. Bu **Çözüm Gezgini** başvurulan derlemenin eksik olduğu projenin proje düğümünü açın.

1. Derlemeyi projeye eklemek için Başvurular klasörünün kısayol menüsünü açın **ve Başvuru** Ekle'yi **seçin.** Başvuru **Ekle iletişim** kutusu görüntülenir.

1. Eklemek istediğiniz başvuruya tıklayın ve ardından Tamam **düğmesini** seçin.

    Başvuru, Başvurular klasörünün altındaki **listeye** eklenir.

1. Ekley istediğiniz derlemenin kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler penceresi görüntülenir.

1. Bu derlemeyi hizmet paketine dahil etmek için, Yereli **Kopyala listesinde** True'yi **seçin.**

1. Web rolü projenize eklenmiş olan dosyaları hizmet paketine eklemek için dosyanın kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler **penceresinde Derleme** Eylemi **liste kutusundan** **İçerik'i** seçin.

1. Çalışan rolü projenize eklenmiş olan dosyaları hizmet paketine eklemek için dosyanın kısayol menüsünü açın ve Özellikler'i **seçin.** Özellikler penceresinde **Çıkış** dizinine **kopyala liste kutusundan** Daha yeni ise **kopyala'yi** seçin.

## <a name="next-steps"></a>Sonraki adımlar

Azure'da yayımlama hakkında daha fazla bilgi Visual Studio bkz. [Azure Uygulama Yayımlama Sihirbazı.](vs-azure-tools-publish-azure-application-wizard.md)
