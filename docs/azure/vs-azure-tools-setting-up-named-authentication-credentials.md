---
title: Adlandırılmış kimlik doğrulama kimlik bilgilerini | Microsoft Docs
description: Azure'da isteklerin Visual Studio kimlik doğrulaması için kullanabileceğiniz kimlik bilgilerini sağlamayı öğrenin. Böylece azure'dan Azure'a Visual Studio veya mevcut bir bulut hizmetini izleyebilirsiniz.
author: ghogen
manager: jmartens
ms.technology: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: e7d8acc861e1460cc569ce6e1bd75ce01bd6e4b4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633038"
---
# <a name="set-up-named-authentication-credentials"></a>Adlandırılmış kimlik doğrulama bilgilerini ayarlama

Bir uygulamayı Azure'da yayımlamak veya mevcut bir bulut hizmetini izlemek için Visual Studio, Azure'a yönelik isteklerin kimliğini doğrulamak için kimlik bilgileri gerektirir. Bu kimlik bilgileri azure abonelik kimliğiniz ve en az 2048 bit anahtara sahip geçerli bir X.509 v3 sertifikası gerektirir. Bu kimlik bilgilerini aşağıdaki yöntemlerden biri aracılığıyla sağlarsiniz:

- Oturum **Visual Studio'> Sunucu Gezgini'** seçin, **Azure** düğümüne sağ tıklayın, Aboneliği **Bağlan'Microsoft Azure seçeneğini** ve oturum açma'yı seçin.
- Sertifika için ortak anahtar içeren bir abonelik dosyası ( `.publishsettings` ) oluşturun. Abonelik dosyası, bu makalede açıklandığı gibi birden fazla aboneliğin kimlik bilgilerini içerebilir.

Not: Bu kimlik bilgileri, Azure depolama hizmetleri için isteklerin kimliğini doğrulamak için kullanılan kimlik bilgilerinden farklıdır.

## <a name="create-a-subscription-file"></a>Abonelik dosyası oluşturma

Bu Sunucu Gezgini Azure düğümüne sağ tıklayın ve **Abonelikleri** Yönet ve **Filtrele'yi seçin.** Ardından **Sertifikalar sekmesini** seçin ve aşağıdaki eylemlerden birini gerçekleştirin:

- İçeri **Aktar'ı** seçerek **Abonelikleri Microsoft Azure iletişim** kutusunu açın. Abonelik **dosyasını indir bağlantısını** seçin ve tarayıcıda indirilen dosyayı geçici bir konuma kaydedin. İletişim kutusuna geri dönüp indirme konumunu açın ve kimlik doğrulamasında kullanmak üzere içeri aktarın.
- Etkin bir abonelik seçin ve **Düzenle'yi** seçin. Bu, mevcut aboneliği kimlik doğrulamasında kullanmak üzere düzenlemek için bir iletişim kutusu açar.
- **Yeni'yi** seçerek **Yeni Abonelik** iletişim kutusunu açın ve gerekli ayrıntıları girin. Sertifikayı bulut hizmetinize yüklemek için iletişim kutusunda not alın, Azure portal'de oturum açın, bulut hizmetinize gidin, **Ayarlar >** Yönetim Sertifikaları'Ayarlar >'yi seçin, **Upload'ı** seçin ve ardından dosyanın yolunu `.cer` belirtin.

Kendiniz bir sertifika oluşturmak için [Azure](/azure/cloud-services/cloud-services-certs-create) için yönetim sertifikası oluşturma ve karşıya yükleme yönergelerine bakabilirsiniz ve ardından sertifikayı el ile [Azure portal.](https://portal.azure.com/)

## <a name="next-steps"></a>Sonraki adımlar

- [Genel bakış Web Apps](/azure/app-service/)
- [Uygulamanızı Azure App Service](/azure/app-service/app-service-deploy-local-git)
- [Visual Studio kullanarak Web İşleri’ni dağıtma](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Bulut hizmeti oluşturma ve dağıtma](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
