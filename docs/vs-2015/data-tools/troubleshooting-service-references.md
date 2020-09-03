---
title: Hizmet başvurularının sorunlarını giderme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: reference
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 60f06aa64cf6a6b96f0c4d610fba1d20b794c55f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667211"
---
# <a name="troubleshooting-service-references"></a>Hizmet Başvurularında Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
Bu konu, [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] içinde veya başvurularıyla çalışırken oluşabilecek yaygın sorunları listeler [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .

## <a name="error-returning-data-from-a-service"></a>Hizmetten veri döndürme hatası
 Bir `DataSet` hizmetten veya bir hizmetten geri döndüğünüzde `DataTable` , "gelen iletiler için en büyük boyut kotası aşıldı" özel durumunu alabilirsiniz. Varsayılan olarak, `MaxReceivedMessageSize` bazı bağlamaların özelliği, hizmet reddi saldırılarına maruz kalma olasılığını sınırlamak için görece küçük bir değere ayarlanır. Özel durumu engellemek için bu değeri artırabilirsiniz.

 Bu hatayı onarmak için:

1. **Çözüm Gezgini**, açmak için app.config dosyasına çift tıklayın.

2. Özelliği bulun `MaxReceivedMessageSize` ve daha büyük bir değerle değiştirin.

## <a name="cannot-find-a-service-in-my-solution"></a>Çözümünüzde bir hizmet bulunamıyor
 **Hizmet başvuruları Ekle** Iletişim kutusunda **bul** düğmesine tıkladığınızda, çözümdeki BIR veya daha fazla WCF hizmet kitaplığı projesi Hizmetler listesinde görünmez. Bu, çözüme bir hizmet kitaplığı eklendiyse ancak henüz derlenmemişse meydana gelebilir.

 Bu hatayı onarmak için:

- **Çözüm Gezgini**, WCF hizmet kitaplığı projesine sağ tıklayın ve **Oluştur**' a tıklayın.

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Uzak Masaüstü üzerinden bir hizmete erişilirken hata oluştu
 Bir Kullanıcı, bir Uzak Masaüstü bağlantısı üzerinden Web 'de barındırılan bir WCF hizmetine eriştiğinde ve kullanıcının yönetim izinleri yoksa, NTLM kimlik doğrulaması kullanılır. Kullanıcı yönetici izinlerine sahip değilse, Kullanıcı şu hata iletisini alabilir: "HTTP isteği, istemci kimlik doğrulama düzeni ' anonim ' ile yetkilendirilmemiş. Sunucudan alınan kimlik doğrulama üst bilgisi ' NTLM ' idi. "

 Bu hatayı onarmak için:

1. Web sitesi projesinde **Özellikler** sayfalarını açın.

2. **Başlangıç seçenekleri** sekmesinde, **NTLM kimlik doğrulaması** onay kutusunu temizleyin.

    > [!NOTE]
    > Yalnızca WCF hizmetleri içeren Web siteleri için NTLM kimlik doğrulamasını kapatmanız gerekir. WCF Hizmetleri için güvenlik, web.config dosyasındaki yapılandırma üzerinden yönetilir. Bu, NTLM kimlik doğrulamasını gereksiz hale getirir.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Oluşturulan sınıflar için erişim düzeyi ayarı etkisizdir
 **Hizmet başvurularını Yapılandır** Iletişim kutusunda **iç** veya **arkadaş** olarak **oluşturulan sınıflar için erişim düzeyi** seçeneğinin ayarlanması her zaman çalışmayabilir. İletişim kutusunda seçenek ayarlanmış gibi görünse de, elde edilen destek sınıfları bir erişim düzeyiyle oluşturulacaktır `Public` .

 Bu, kullanılarak serileştirilenler gibi belirli türlerin bilinen bir sınırlamasıdır <xref:System.Xml.Serialization.XmlSerializer> .

## <a name="error-debugging-service-code"></a>Hizmet kodunda hata ayıklama hatası
 İstemci kodundan bir WCF hizmeti için kod içine adımlayın, eksik simgelerle ilgili bir hata alabilirsiniz. Bu, çözümünüzün parçası olan bir hizmet çözümden taşındığında veya kaldırıldığında gerçekleşebilir.

 Geçerli çözümün parçası olan bir WCF hizmetine ilk kez başvuru eklediğinizde, hizmet projesi ve hizmet istemci projesi arasında açık bir derleme bağımlılığı eklenir. Bu, istemcinin, istemci kodundan hizmet koduna atlama gibi hata ayıklama senaryoları için önemli olan güncel hizmet ikililerini her zaman erişmesi güvence altına alır.

 Hizmet projesi çözümden kaldırılırsa, bu açık derleme bağımlılığı geçersiz kılınır. Visual Studio artık hizmet projesinin gerektiği şekilde yeniden oluşturulmasını garanti etmez.

 Bu hatayı onarmak için, hizmet projesini el ile yeniden oluşturmanız gerekir:

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. **Seçenekler** iletişim kutusunda, **Projeler ve çözümler**' i genişletin ve ardından **genel**' i seçin.

3. **Gelişmiş derleme yapılandırmasını göster** onay kutusunun seçili olduğundan emin olun ve ardından **Tamam**' a tıklayın.

4. WCF hizmeti projesini yükleyin. Daha fazla bilgi için bkz. [nib nasıl yapılır: birden çok projeli çözüm oluşturma](https://msdn.microsoft.com/02ecd6dd-0114-46fe-b335-ba9c5e3020d6).

5. **Configuration Manager** iletişim kutusunda, **etkin çözüm yapılandırmasını** **Hata Ayıkla**olarak ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: yapılandırma oluşturma ve düzenleme](../ide/how-to-create-and-edit-configurations.md).

6. **Çözüm Gezgini**, WCF hizmeti projesini seçin.

7. WCF hizmeti projesini yeniden derlemek için **Derle** menüsünde **yeniden derle** ' ye tıklayın.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Veri Hizmetleri tarayıcıda gösterme
 Internet Explorer verilerin bir XML temsilini görüntülemeye çalıştığında [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] verileri BIR RSS akışı olarak yanlış yorumlayabilir. RSS akışlarını görüntüleme seçeneğinin devre dışı bırakıldığından emin olmalısınız.

 Bu hatayı onarmak için RSS akışlarını devre dışı bırakın:

1. Internet Explorer 'da, **Araçlar** menüsünde **Internet seçenekleri**' ne tıklayın.

2. **İçerik** sekmesinde, **akışlar** bölümünde, **Ayarlar**' a tıklayın.

3. **Akış ayarları** iletişim kutusunda, **akış okuma görünümünü aç** onay kutusunu temizleyin ve ardından **Tamam**' a tıklayın.

4. **Internet seçenekleri** iletişim kutusunu kapatmak için **Tamam** ' ı tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)