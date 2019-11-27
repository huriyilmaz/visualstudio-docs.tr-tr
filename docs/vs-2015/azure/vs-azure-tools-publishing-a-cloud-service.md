---
title: Azure araçlarını kullanarak bir bulut hizmeti yayımlama | Microsoft Docs
description: Visual Studio kullanarak Azure Cloud Service projelerini yayımlama hakkında bilgi edinin.
author: ghogen
manager: jillfra
assetId: 1a07b6e4-3678-4cbf-b37e-4520b402a3d9
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: f382226ab20053a57b10326853f16e27f641b3be
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298120"
---
# <a name="publishing-a-cloud-service-using-visual-studio"></a>Visual Studio kullanarak bulut hizmetini yayımlama

Visual Studio, bir bulut hizmetinin hem hazırlık hem de üretim ortamları için destek sayesinde bir uygulamayı doğrudan Azure 'da yayımlayabilir. Yayımlarken, dağıtım paketini ve dağıtım paketi için geçici olarak kullanılan bir depolama hesabını seçersiniz.

Bir Azure uygulaması geliştirirken ve sınadığınızda, değişiklikleri Web rolleriniz için artımlı olarak yayımlamak üzere Web Dağıtımı kullanabilirsiniz. Uygulamanızı bir dağıtım ortamında yayımladıktan sonra, Web Dağıtımı değişiklikleri doğrudan Web rolünü çalıştıran sanal makineye dağıtmanızı sağlar. Değişiklikleri test etmek için Web rolünüzü güncelleştirmek istediğiniz her seferinde tüm Azure uygulamanızı paketleyip yayımlamanız gerekmez. Bu yaklaşımla, uygulamanızın bir dağıtım ortamında yayımlanmasını beklemeden, test için Web rolünüzün değişikliklerinizin bulutta kullanılabilmesini sağlayabilirsiniz.

Azure uygulamanızı yayımlamak ve Web Dağıtımı kullanarak bir Web rolünü güncelleştirmek için aşağıdaki yordamları kullanın:

- Visual Studio 'dan bir Azure uygulaması yayımlama veya paketleme
- Geliştirme ve test döngüsünün bir parçası olarak bir Web rolünü güncelleştirme

## <a name="publish-or-package-an-azure-application-from-visual-studio"></a>Visual Studio 'dan bir Azure uygulaması yayımlama veya paketleme

Azure uygulamanızı yayımladığınızda, aşağıdaki görevlerden birini yapabilirsiniz:

- Bir hizmet paketi oluşturun: uygulamanızı [Azure Portal](https://portal.azure.com)bir dağıtım ortamında yayımlamak için bu paketi ve hizmet yapılandırma dosyasını kullanabilirsiniz.

- Azure projenizi Visual Studio 'dan yayımlayın: uygulamanızı doğrudan Azure 'da yayımlamak Için, Yayımlama Sihirbazı 'nı kullanın. Bilgi için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).

### <a name="to-create-a-service-package-from-visual-studio"></a>Visual Studio 'dan bir hizmet paketi oluşturmak için

1. Uygulamanızı yayımlamaya hazırsanız Çözüm Gezgini açın, rollerinizi içeren Azure projesi için kısayol menüsünü açın ve Yayımla ' yı seçin.

1. Yalnızca bir hizmet paketi oluşturmak için aşağıdaki adımları izleyin:

   a. Azure projesinin kısayol menüsünde **paket**' i seçin.

   b. **Paket Azure uygulaması** iletişim kutusunda, paket oluşturmak istediğiniz hizmet yapılandırmasını seçin ve ardından yapı yapılandırmasını seçin.

   c. Seçim Yayımladıktan sonra bulut hizmeti için Uzak Masaüstü 'Nü açmak üzere **tüm roller Için uzak masaüstünü etkinleştir**' i seçin ve ardından Uzak Masaüstü kimlik bilgilerini yapılandırmak için **Ayarlar** ' ı seçin. Daha fazla bilgi için bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

      Yayımladıktan sonra bulut hizmetinizde hata ayıklamak istiyorsanız, uzaktan hata ayıklamayı **tüm roller Için etkinleştir**' i seçerek açın.

   d. Paketi oluşturmak için **paket** bağlantısını seçin.

      Dosya Gezgini, yeni oluşturulan paketin dosya konumunu gösterir. Bu konumu, Azure portal kullanabilmek için kopyalayabilirsiniz.

   e. Bu paketi bir dağıtım ortamında yayımlamak için, bir bulut hizmeti oluştururken ve bu paketi Azure portal bir ortama dağıttığınızda paket konumu olarak bu konumu kullanmanız gerekir.

1. Seçim Dağıtım işlemini iptal etmek için, etkinlik günlüğündeki satır öğesi için kısayol menüsünde **iptal ve Kaldır**' ı seçin. Bu komut, dağıtım işlemi durdurur ve Azure'dan dağıtım ortamı siler. Dağıtımı tamamladıktan sonra ortamı kaldırmak için Azure portal kullanın.

1. Seçim Rol örneklerinizin başlatılmasından sonra, Visual Studio Sunucu Gezgini içindeki **Cloud Services** düğümünde dağıtım ortamını otomatik olarak gösterir. Buradan, tek tek rol örneklerinin durumunu görebilirsiniz. Bkz. [bulut Gezgini Ile Azure kaynaklarını yönetme](vs-azure-tools-resources-managing-with-cloud-explorer.md). Aşağıdaki çizimde, hala başlatma durumunda olan rol örnekleri gösterilmektedir:

    ![VST_DeployComputeNode](./media/vs-azure-tools-publishing-a-cloud-service/IC744134.png)

## <a name="update-a-web-role-as-part-of-the-development-and-testing-cycle"></a>Geliştirme ve test döngüsünün bir parçası olarak bir Web rolünü güncelleştirme

Uygulamanızın arka uç altyapısı kararlı ise, ancak Web rollerinin daha sık güncelleştirilmesi gerekiyorsa, projenizdeki yalnızca bir Web rolünü güncelleştirmek için Web Dağıtımı kullanabilirsiniz. Web Dağıtımı, arka uç çalışan rollerini yeniden oluşturmak ve yeniden dağıtmak istemediğinizde veya birden fazla Web rolüne sahipseniz ve yalnızca bir web rolünden yalnızca birini güncellemek istediğinizde yararlı olur.

### <a name="requirements-for-using-web-deploy"></a>Web Dağıtımı kullanma gereksinimleri

- **Yalnızca geliştirme ve test amaçlıdır**: değişiklikler doğrudan Web rolünün çalıştığı sanal makineye yapılır. Bu sanal makinenin geri dönüştürülmesi gerekiyorsa, değişiklikler kaybedilir çünkü yayımladığınız özgün paket, rol için sanal makineyi yeniden oluşturmak için kullanılır. Web rolü için en son değişiklikleri almak üzere uygulamanızı yeniden yayımlayın.

- **Yalnızca Web rolleri güncelleştirilemiyor**: çalışan rolleri güncelleştirilemiyor. Ayrıca, `web role.cs``RoleEntryPoint` güncelleştiremezsiniz.

- **Bir Web rolünün yalnızca tek bir örneğini destekleyebilir**: dağıtım ortamınızda herhangi bir Web rolünün birden çok örneği olamaz. Ancak, her biri yalnızca bir örneğe sahip birden çok web rolü desteklenir.

- **Uzak Masaüstü bağlantılarını etkinleştir**: Bu gereksinim, Web dağıtımı Internet INFORMATION SERVICES (IIS) çalıştıran sunucuya değişiklikleri dağıtmak üzere sanal makineye bağlanmak için Kullanıcı ve parolayı kullanmasına izin verir. Ayrıca, bu sanal makinede IIS 'ye güvenilir bir sertifika eklemek için sanal makineye bağlanmanız gerekebilir. (Bu sertifika, Web Dağıtımı tarafından kullanılan IIS için Uzak bağlantının güvende olmasını sağlar.)

Aşağıdaki yordamda, **Azure uygulama yayımlama** Sihirbazı 'nı kullandığınız varsayılır.

### <a name="enable-web-deploy-when-you-publish-your-application"></a>Uygulamanızı yayımladığınızda Web Dağıtımı etkinleştirme

1. **Tüm Web rolleri için Web dağıtımı etkinleştir** seçeneğini etkinleştirmek için öncelikle Uzak Masaüstü bağlantıları 'nı yapılandırmanız gerekir. Tüm roller için **uzak masaüstünü etkinleştir** ' i seçin ve görüntülenen **Uzak Masaüstü yapılandırması** kutusuna uzaktan bağlanmak için kullanılan kimlik bilgilerini sağlayın. Bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio).

1. Uygulamanızdaki tüm Web rolleri için Web Dağıtımı etkinleştirmek üzere **tüm Web rolleri için Web dağıtımı etkinleştir**' i seçin.

    Sarı bir uyarı üçgeni belirir. Web Dağıtımı, varsayılan olarak güvenilir olmayan, otomatik olarak imzalanan bir sertifika kullanır ve bu, hassas verileri karşıya yüklemek için önerilmez. Bu işlemi hassas veriler için güvenli hale getirmeniz gerekiyorsa Web Dağıtımı bağlantıları için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifikanın güvenilir bir sertifika olması gerekir. Daha fazla bilgi için bkz. [Web dağıtımı güvenli hale getirme](#make-web-deploy-secure).

1. **Özet** ekranını göstermek için **İleri** ' yi, sonra da bulut hizmetini dağıtmak için **Yayımla** ' yı seçin.

    Bulut hizmeti yayımlandı. Oluşturulan sanal makinede, Web rollerinizi yeniden yayımlamadan güncelleştirmek için Web Dağıtımı IIS için uzak bağlantılar etkinleştirilmiş olmalıdır.

   > [!NOTE]
   > Bir Web rolü için yapılandırılmış birden fazla örneğiniz varsa, her bir Web rolünün yalnızca uygulamanızı yayımlamak için oluşturulan pakette bir örnekle sınırlı olduğunu belirten bir uyarı iletisi görüntülenir. Devam etmek için **Tamam ' ı** seçin. Gereksinimler bölümünde belirtildiği gibi, birden fazla Web rolüne sahip olabilirsiniz ancak her rolün yalnızca bir örneği olabilir.

### <a name="update-your-web-role-by-using-web-deploy"></a>Web rolünüzü Web Dağıtımı kullanarak güncelleştirin

1. Web Dağıtımı kullanmak için, yayımlamak istediğiniz Visual Studio 'daki Web rollerinizin herhangi biri için projede kod değişiklikleri yapın ve ardından çözümünüzde bu proje düğümüne sağ tıklayıp **Yayımla**' yı işaret edin. **Web 'ı Yayımla** iletişim kutusu görüntülenir.

1. Seçim IIS için uzak bağlantılar için kullanmak üzere güvenilen bir SSL sertifikası eklediyseniz, **Güvenilmeyen sertifikaya Izin ver** onay kutusunu temizleyebilirsiniz. Web Dağıtımı güvenli hale getirmek için bir sertifika ekleme hakkında daha fazla bilgi için, bu makalede daha sonra **Web dağıtımı güvenli hale getirmek için** bölümüne bakın.

1. Web Dağıtımı kullanmak için, yayınlama mekanizmasına, paketi ilk yayımlandığında, uzak masaüstü bağlantınız için ayarladığınız Kullanıcı adı ve parola gerekir.

   a. **Kullanıcı adı**alanına kullanıcı adını girin.

   b. **Parola**alanına parolayı girin.

   c. Seçim Bu parolayı bu profilde kaydetmek istiyorsanız, **Parolayı kaydet**' i seçin.

1. Değişiklikleri Web rolünüzde yayımlamak için **Yayımla**' yı seçin.

    Durum satırı **Yayımlama başladı**' i görüntüler. Yayımlama tamamlandığında, **Yayımlama başarılı** görüntülenir. Değişiklikler artık sanal makinenizde Web rolüne dağıtıldı. Şimdi yaptığınız değişiklikleri test etmek için Azure uygulamanızı Azure ortamında başlatabilirsiniz.

### <a name="make-web-deploy-secure"></a>Web dağıtımı güvenli hale getirme

1. Web Dağıtımı, varsayılan olarak güvenilir olmayan, otomatik olarak imzalanan bir sertifika kullanır ve bu, hassas verileri karşıya yüklemek için önerilmez. Bu işlemi hassas veriler için güvenli hale getirmeniz gerekiyorsa Web Dağıtımı bağlantıları için kullanılacak bir SSL sertifikası ekleyebilirsiniz. Bu sertifikanın bir sertifika yetkilisinden (CA) edindiğiniz güvenilir bir sertifika olması gerekir.

    Web rollerinizin her biri için her bir sanal makine için Web Dağıtımı güvenli hale getirmek üzere, Web dağıtımı için kullanmak istediğiniz güvenilen sertifikayı Azure portal yüklemeniz gerekir. Bu sertifika, uygulamanızı yayımladığınızda web rolü için oluşturulan sanal makineye sertifikanın eklendiğinden emin olmanızı sağlar.

1. Uzaktan bağlantılar için kullanmak üzere IIS 'ye güvenilir bir SSL sertifikası eklemek için aşağıdaki adımları izleyin:

   a. Web rolünü çalıştıran sanal makineye bağlanmak için, **Cloud Explorer** veya **Sunucu Gezgini**web rolü örneğini seçin ve ardından **Uzak Masaüstü kullanarak bağlan** komutunu seçin. Sanal makineye bağlanma hakkında ayrıntılı adımlar için bkz. [Visual Studio kullanarak Azure Cloud Services bir rol için Uzak Masaüstü bağlantısı etkinleştirme](/azure/cloud-services/cloud-services-role-enable-remote-desktop-visual-studio). Tarayıcınız bir `.rdp` dosyası indirmenizi ister.

   b. Bir SSL sertifikası eklemek için, Yönetim hizmetini IIS Yöneticisi ' nde açın. IIS Yöneticisi 'nde, **eylem** bölmesinde **bağlamalar** bağlantısını açarak SSL 'yi etkinleştirin. **Site Bağlaması Ekle** iletişim kutusu görüntülenir. **Ekle**' yi seçin ve ardından **tür** açılan listesinden HTTPS ' yi seçin. **SSL sertifikası** listesinde, bir CA tarafından imzaladığınız ve Azure Portal yüklediğiniz SSL sertifikasını seçin. Daha fazla bilgi için bkz. [Yönetim hizmeti Için bağlantı ayarlarını yapılandırma](https://go.microsoft.com/fwlink/?LinkId=215824).

      > [!NOTE]
      > Güvenilen bir SSL sertifikası eklerseniz, daha sonra, **Yayımlama sihirbazında**sarı uyarı üçgeni görünmez.

## <a name="include-files-in-the-service-package"></a>Hizmet paketine dosya ekleme

Bir rol için oluşturulan sanal makinede kullanılabilir olmaları için hizmet paketinizdeki belirli dosyaları eklemeniz gerekebilir. Örneğin, hizmet paketinize bir başlangıç betiği tarafından kullanılan bir `.exe` veya `.msi` dosyası eklemek isteyebilirsiniz. Ya da bir Web rolü veya çalışan rolü projesinin gerektirdiği bir derleme eklemeniz gerekebilir. Dosyaları dahil etmek için, Azure uygulamanız için çözüme eklenmeleri gerekir.

1. Bir hizmet paketine bir derleme eklemek için aşağıdaki adımları kullanın:

   a. **Çözüm Gezgini**, başvurulan derlemenin eksik olduğu proje için proje düğümünü açın.
   b. Derlemeyi projeye eklemek için, **Başvurular** klasörünün kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin. Başvuru Ekle iletişim kutusu görünür.
   c. Eklemek istediğiniz başvuruyu seçin ve ardından **Tamam**' ı seçin. Başvuru, **Başvurular** klasörü altındaki listeye eklenir.
   d. Eklediğiniz derlemenin kısayol menüsünü açın ve **Özellikler**' i seçin. **Özellikler** penceresi görüntülenir.

      Bu derlemeyi hizmet paketine eklemek için, **Yerel Kopyala listesinde** **doğru**öğesini seçin.
1. **Çözüm Gezgini** başvurulan derleme eksik olan proje için proje düğümünü açın.

1. Derlemeyi projeye eklemek için, **Başvurular** klasörünün kısayol menüsünü açın ve ardından **Başvuru Ekle**' yi seçin. **Başvuru Ekle** iletişim kutusu görünür.

1. Eklemek istediğiniz başvuruyu seçin ve sonra **Tamam** düğmesini seçin.

    Başvuru, **Başvurular** klasörü altındaki listeye eklenir.

1. Eklediğiniz derlemenin kısayol menüsünü açın ve **Özellikler**' i seçin. Özellikler penceresi görüntülenir.

1. Bu derlemeyi hizmet paketine eklemek için, **Yerel Kopyala** listesinde, **doğru**öğesini seçin.

1. Web rolü projenize eklenmiş olan hizmet paketine dosyaları eklemek için, dosyanın kısayol menüsünü açın ve **Özellikler**' i seçin. **Özellikler** penceresinde, **Yapı eylemi** liste kutusunda **içerik** ' i seçin.

1. Çalışan rolü projenize eklenmiş olan hizmet paketine dosyaları eklemek için, dosyanın kısayol menüsünü açın ve **Özellikler**' i seçin. **Özellikler** penceresinden, **Çıkış Dizinine Kopyala** liste kutusunda **daha yeniyse kopyala** ' yı seçin.

## <a name="next-steps"></a>Sonraki adımlar

Visual Studio 'dan Azure 'da yayımlama hakkında daha fazla bilgi edinmek için bkz. [Azure Uygulama Yayımlama Sihirbazı](vs-azure-tools-publish-azure-application-wizard.md).
