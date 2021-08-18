---
title: Hizmet Başvurularında Sorun Giderme
description: Windows Communication Foundation (WCF) ile çalışırken veya WCF Veri Hizmetleri başvurularını gözden Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- msvse_wcf.Err.ReferenceGroup_NamespaceConflictsOther
- msvse_wcf.Err.AddSvcRefDlg_NothingSelectedOnGo
- msvse_wcf.Err.ErrorOnOK
- msvse_wcf.cfg.ConfigurationErrorsException
helpviewer_keywords:
- service references [Visual Studio], troubleshooting
- WCF services, troubleshooting
ms.assetid: 3b531120-1325-4734-90c6-6e6113bd12ac
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 649204a074980c547fc238ba0c7db923c7ff199b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031607"
---
# <a name="troubleshoot-service-references"></a>Hizmet başvurularında sorun giderme

Bu konuda, Windows Communication Foundation (WCF) veya WCF Veri Hizmetleri iletişim Visual Studio.

## <a name="error-returning-data-from-a-service"></a>Hizmetten veri döndürürken hata oluştu

Bir hizmetten veya iade ediyorsanız ,"Gelen iletiler için en yüksek boyut kotası `DataSet` `DataTable` aşıldı" özel durumu alabilirsiniz. Varsayılan olarak, bazı bağlamaların özelliği hizmet reddi saldırılarına maruz kalmayı sınırlamak için `MaxReceivedMessageSize` görece küçük bir değere ayarlanır. Özel durumu önlemek için bu değeri artırabilir. Daha fazla bilgi için bkz. <xref:System.ServiceModel.HttpBindingBase.MaxReceivedMessageSize%2A>.

Bu hatayı düzeltmek için:

1. Bu **Çözüm Gezgini,** dosyanınapp.config *çift* tıklar.

2. özelliğini `MaxReceivedMessageSize` bulun ve daha büyük bir değerle değiştirebilirsiniz.

## <a name="cannot-find-a-service-in-my-solution"></a>Çözümümde hizmet bulamıyorum

Hizmet Başvuruları **Ekle** iletişim  kutusunda Keşfet düğmesine tıklarken, çözümdeki bir veya daha fazla WCF Hizmet Kitaplığı projesi hizmetler listesinde görünmez. Çözüme bir Hizmet Kitaplığı eklenmiştir ancak henüz derlenmiş durumda değildir.

Bu hatayı düzeltmek için:

- Bu **Çözüm Gezgini** WCF Hizmet Kitaplığı projesine sağ tıklayın ve Derleme'ye **tıklayın.**

## <a name="error-accessing-a-service-over-a-remote-desktop"></a>Uzak masaüstü üzerinden hizmete erişme hatası

Bir kullanıcı, uzak masaüstü bağlantısı üzerinden Web'de barındırılan bir WCF hizmetine erişenin ve kullanıcının yönetim izinleri yoksa, NTLM kimlik doğrulaması kullanılır. Kullanıcının yönetici izinleri yoksa, kullanıcı şu hata iletisini alabilirsiniz: "HTTP isteği, 'Anonim' istemci kimlik doğrulama düzeniyle yetkisiz. Sunucudan alınan kimlik doğrulama üst bilgisi "NTLM" şeklindedir.

Bu hatayı düzeltmek için:

1. Web sitesi projesinde Özellikler **sayfalarını** açın.

2. Başlatma **Seçenekleri sekmesinde** **NTLM** Kimlik Doğrulaması onay kutusunun işaretini kaldırın.

    > [!NOTE]
    > NTLM kimlik doğrulamasını yalnızca yalnızca WCF hizmetlerini içeren web siteleri için kapatabilirsiniz. WCF hizmetleri için güvenlik,web.config *dosyasındaki yapılandırma aracılığıyla* yönetilir. Bu, NTLM kimlik doğrulamasını gereksiz hale verir.

## <a name="access-level-for-generated-classes-setting-has-no-effect"></a>Oluşturulan sınıflar için erişim düzeyi ayarının hiçbir etkisi yoktur

Hizmet **Başvurularını Yapılandır iletişim kutusundaki**  oluşturulan sınıflar için Erişim  düzeyini İç veya Arkadaş olarak ayarlama **her** zaman çalışmayabilirsiniz. seçeneği iletişim kutusunda ayarlanmış gibi görünüyor olsa da, sonuçta elde edilen destek sınıfları erişim düzeyiyle `Public` oluşturulur.

Bu, kullanılarak seri hale getirilecekler gibi belirli türlerin bilinen bir <xref:System.Xml.Serialization.XmlSerializer> sınırlamasıdır.

## <a name="error-debugging-service-code"></a>Hizmet kodunda hata ayıklama hatası

İstemci kodundan BIR WCF hizmetinin koduna adım adım, eksik sembollerle ilgili bir hata alabilirsiniz. Çözüme parçası olan bir hizmet çözümden taşındığında veya kaldırıldığı zaman bu durum oluşabilir.

Geçerli çözümün parçası olan bir WCF hizmetine ilk kez başvuru eklerken, hizmet projesi ile hizmet istemcisi projesi arasına açık bir derleme bağımlılığı eklenir. Bu, istemcinin her zaman güncel hizmet ikililerine erişmesini garantiler. Bu, özellikle istemci kodundan hizmet koduna adımlama gibi senaryolarda hata ayıklama için önemlidir.

Hizmet projesi çözümden kaldırılırsa, bu açık derleme bağımlılığı geçersiz kılınmış olur. Visual Studio artık hizmet projesinin gerektiği gibi yeniden oluşturulmuş olduğunu garanti edilemez.

Bu hatayı düzeltmek için hizmet projesini el ile yeniden oluşturmanız gerekir:

1. **Tools** (Araçlar) menüsünde **Options**’a (Seçenekler) tıklayın.

2. Seçenekler iletişim **kutusunda** Projeler ve Çözümler'i **genişletin ve** ardından Genel'i **seçin.**

3. Gelişmiş derleme yapılandırmalarını **göster onay kutusunun seçili** olduğundan emin olun ve ardından Tamam'a **tıklayın.**

4. WCF hizmet projesini yükleme.

5. Yapılandırma Yöneticisi **iletişim** kutusunda Etkin çözüm **yapılandırmasını Hata Ayıkla** **olarak ayarlayın.** Daha fazla bilgi için, [bkz. How to: Create and edit configurations](../ide/how-to-create-and-edit-configurations.md).

6. Bu **Çözüm Gezgini** WCF hizmeti projesini seçin.

7. WcF **hizmeti projesini** yeniden oluşturmak **için Derleme** menüsünde Yeniden Oluştur'a tıklayın.

## <a name="wcf-data-services-do-not-display-in-the-browser"></a>WCF Veri Hizmetleri tarayıcıda görüntülenmez

bir dosyasındaki verilerin XML gösterimini görüntülemeye Internet Explorer RSS akışı olarak yanlış yorumlayan veriler [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] olabilir. RSS akışlarını görüntüleme seçeneğinin devre dışı bırakıldı olduğundan emin olun.

Bu hatayı düzeltmek için RSS akışlarını devre dışı bırak:

1. Bu Internet Explorer Araçlar menüsünde **İnternet** **Seçenekleri'ne tıklayın.**

2. İçerik **sekmesinde,** Akışlar **bölümünde,** Akışlar'a **Ayarlar.**

3. Akış **Ayarlar** iletişim kutusunda Akış okuma görünümünü **aç onay** kutusunun işaretini kaldırın ve ardından Tamam'a **tıklayın.**

4. İnternet **Seçenekleri** iletişim kutusunu kapatmak **için Tamam'a** tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
