---
title: 'Nasıl Yapılır: Bağlantı Dizelerini Kaydetme ve Düzenleme'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ed0f0105383667e1122d6636a3baab3aa925a742
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586464"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Nasıl yapılır: bağlantı dizelerini kaydetme ve düzenleme
Visual Studio uygulamalarındaki bağlantı dizeleri uygulama yapılandırma dosyasına (uygulama ayarları olarak da anılır) veya doğrudan uygulamanızda sabit kodlanmış olarak kaydedilir. Bağlantı dizelerini uygulama yapılandırma dosyasına kaydetmek, uygulamanızı sürdürme görevini basitleştirir. Bağlantı dizesinin değiştirilmesi gerekiyorsa, bunu uygulama ayarları dosyasında güncelleştirebilirsiniz (kaynak kodda değiştirmek ve uygulamayı yeniden derlemek zorunda kalmak yerine).

Bağlantı dizesinde gizli bilgilerin (parola gibi) depolanması, uygulamanızın güvenliğini etkileyebilir. Uygulama yapılandırma dosyasına kaydedilen bağlantı dizeleri şifrelenmez veya görünmez, bu nedenle birisinin dosyaya erişmesi ve içeriğini görüntülemesi mümkün olabilir. Windows tümleşik güvenliği 'nin kullanılması, bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.

Windows tümleşik güvenliğini kullanmayı tercih ederseniz, veritabanınız bir Kullanıcı adı ve parola gerektiriyorsa, bunları bağlantı dizesinden çıkarabilirsiniz, ancak uygulamanızın veritabanına başarıyla bağlanması için bu bilgileri sağlaması gerekir. Örneğin, kullanıcıya bu bilgileri isteyen bir iletişim kutusu oluşturabilir ve bağlantı dizesini çalışma zamanında dinamik olarak oluşturur. Bilgiler, veritabanının yolunda ele alınıp devam ediyorsa sorun olabilir.
Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Veri kaynağı Yapılandırma Sihirbazı içinden bir bağlantı dizesini kaydetmek için
**Veri kaynağı Yapılandırma Sihirbazı**' nda, bağlantı **dizesini uygulama yapılandırma dosyasına kaydet** sayfasına bağlantıyı kaydetme seçeneğini belirleyin.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Bağlantı dizesini doğrudan uygulama ayarlarına kaydetmek için
1. **Çözüm Gezgini**, proje **tasarımcısını**açmak için **projem** simgesine (Visual Basic) veya **Özellikler** simgesine (C#) çift tıklayın.
1. Seçin **ayarları** sekmesi.
1. Bağlantı dizesi için bir **ad** girin. Koddaki bağlantı dizesine erişirken bu adı inceleyin.
1. **Türü** (**bağlantı dizesi**) olarak ayarlayın.
1. **Kapsamı** **uygulama**olarak ayarlayın.
1. **Değer** alanına bağlantı dizenizi yazın veya Bağlantı dizenizi derlemek Için **bağlantı özellikleri** Iletişim kutusunu açmak üzere **değer** alanındaki **üç nokta** (...) düğmesine tıklayın.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Uygulama ayarlarında depolanan bağlantı dizelerini Düzenle
**Proje tasarımcısını**kullanarak uygulama ayarlarına kaydedilen bağlantı bilgilerini değiştirebilirsiniz.

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Uygulama ayarlarında depolanan bir bağlantı dizesini düzenlemek için
1. **Çözüm Gezgini**, proje **tasarımcısını**açmak için **projem** simgesine (Visual Basic) veya **Özellikler** simgesine (C#) çift tıklayın.
1. Seçin **ayarları** sekmesi.
1. Düzenlemek istediğiniz bağlantıyı bulun ve **değer** alanındaki metni seçin.
1. **Değer** alanındaki bağlantı dizesini düzenleyin veya bağlantı **özellikleri** iletişim kutusuyla bağlantınızı düzenlemek için **değer** alanındaki **üç nokta** (...) düğmesine tıklayın.

## <a name="edit-connection-strings-for-datasets"></a>Veri kümeleri için bağlantı dizelerini düzenleme
Bir veri kümesindeki her bir TableAdapter için bağlantı bilgilerini değiştirebilirsiniz.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Veri kümesindeki bir TableAdapter için bağlantı dizesini düzenlemek için
1. **Çözüm Gezgini**, düzenlemek istediğiniz bağlantıyı içeren veri kümesine ( **. xsd** dosyası) çift tıklayın.
1. Düzenlemek istediğiniz bağlantıyı içeren **TableAdapter** veya sorguyu seçin.
1. **Özellikler** penceresinde **bağlantı düğümünü**genişletin.
1. Bağlantı dizesini hızlıca değiştirmek için **ConnectionString** özelliğini düzenleyin veya **bağlantı** özelliğindeki aşağı oka tıklayın ve **Yeni bağlantı**' yı seçin.

## <a name="security"></a>Güvenlik
Bağlantı dizesinin içindeki hassas bilgilerin (parola gibi) depolanması, uygulamanızın güvenliğini etkileyebilir. Windows tümleşik güvenliği 'nin kullanılması, bir veritabanına erişimi denetlemek için daha güvenli bir yoldur.
Daha fazla bilgi için bkz. [bağlantı bilgilerini koruma](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)
