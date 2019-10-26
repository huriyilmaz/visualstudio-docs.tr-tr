---
title: Adlandırılmış kimlik doğrulama kimlik bilgilerini ayarlama | Microsoft Docs
description: Visual Studio 'Nun Azure 'a yönelik isteklerin kimliğini doğrulamak için kullanabileceği kimlik bilgilerini nasıl sağlayacağınızı öğrenin. böylece, Azure 'da bir uygulamayı Visual Studio 'dan yayımlayabilir veya var olan bir bulut hizmetini izleyebilirsiniz.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 57841baaf147c2aae02ac89a8401c46d3bd64ca3
ms.sourcegitcommit: 257fc60eb01fefafa9185fca28727ded81b8bca9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72911677"
---
# <a name="set-up-named-authentication-credentials"></a>Adlandırılmış kimlik doğrulama bilgilerini ayarlama

Bir uygulamayı Azure 'da yayınlamak veya var olan bir bulut hizmetini izlemek için, Visual Studio Azure abonelik KIMLIĞINIZ ve en az 2048 bitlik bir anahtarla geçerli bir X. 509.440 v3 sertifikası olmak üzere Azure 'Da isteklerin kimliğini doğrulamak için kimlik bilgileri gerektirir. Aşağıdaki yöntemlerden birini kullanarak bu kimlik bilgilerini sağlarsınız:

- Visual Studio 'da **görünüm > Sunucu Gezgini**seçin, **Azure** düğümüne sağ tıklayın, **Microsoft Azure aboneliğine Bağlan**' ı seçin ve oturum açın.
- Sertifika için ortak anahtar içeren bir abonelik dosyası (`.publishsettings`) oluşturun. Abonelik dosyası, bu makalede açıklandığı gibi birden fazla abonelik için kimlik bilgileri içerebilir.

Note: Bu kimlik bilgileri, Azure depolama hizmetlerine yönelik isteklerin kimliğini doğrulamak için kullanılan kimlik bilgilerinden farklıdır.

## <a name="create-a-subscription-file"></a>Abonelik dosyası oluşturma

Sunucu Gezgini, **Azure** düğümüne sağ tıklayın ve **abonelikleri Yönet ve filtrele**' yi seçin. Ardından **Sertifikalar** sekmesini seçin ve ardından aşağıdaki eylemlerden birini yapın:

- **Microsoft Azure abonelikleri Içeri aktar** iletişim kutusunu açmak Için **içeri aktar** ' ı seçin. **Abonelik dosyasını indir** bağlantısını seçin ve tarayıcıda indirilen dosyayı geçici bir konuma kaydedin. İletişim kutusuna geri dönüp indirme konumuna gidin ve kimlik doğrulamasında kullanmak için içeri aktarın.
- Etkin bir abonelik seçin ve kimlik doğrulamasında kullanılmak üzere mevcut bir aboneliği düzenlediğiniz bir iletişim kutusu açan **Düzenle**' yi seçin.
- Yeni **abonelik** iletişim kutusunu açmak için **Yeni** ' yi seçin ve gereken ayrıntıları sağlayın. Sertifikayı bulut hizmetinize yüklemek için iletişim kutusunda, Azure portal oturum açın, bulut hizmetinize gidin, **ayarlar > yönetim sertifikaları**' nı seçin, **Yükle**' yi seçin ve `.cer` dosyasının yolunu belirtin.

Kendiniz bir sertifika oluşturmak isterseniz, [Azure için bir yönetim sertifikası oluşturma ve yükleme](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) ' deki yönergelere başvurabilirsiniz ve sonra sertifikayı [Azure Portal](https://portal.azure.com/)el ile yükleyebilirsiniz.

## <a name="next-steps"></a>Sonraki adımlar

- [Web Apps genel bakış](/azure/app-service/)
- [Uygulamanızı Azure App Service dağıtma](/azure/app-service/app-service-deploy-local-git)
- [Visual Studio kullanarak Web Işleri dağıtma](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Bulut hizmeti oluşturma ve dağıtma](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
