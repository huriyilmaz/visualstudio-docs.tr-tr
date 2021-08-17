---
title: 'Nasıl Yapılır: Bağlantı Dizelerini Kaydetme ve Düzenleme'
description: Uygulama uygulamalarında bağlantı dizelerini kaydetmeyi ve düzenlemeyi Visual Studio olun. Bağlantı dizesini doğrudan uygulama ayarlarında kaydedin veya düzenleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: f8ef3a2c-029c-423b-9d9e-a4f1add4f640
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 440a9b9458d0357235489d69a75e9e9980aa6a3adbe9d513241455d0af751336
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347070"
---
# <a name="how-to-save-and-edit-connection-strings"></a>Nasıl: Bağlantı dizelerini kaydetme ve düzenleme
Uygulama yapılandırma Visual Studio bağlantı dizeleri uygulama yapılandırma dosyasına kaydedilir (uygulama ayarları olarak da adlandırılır) veya doğrudan uygulamanıza sabit kodlu olarak kaydedilir. Bağlantı dizelerini uygulama yapılandırma dosyasına kaydetme, uygulamanın bakımının basitleştirilmesini sağlar. Bağlantı dizesinin değişmesi gerekirse, bunu uygulama ayarları dosyasında güncelleştirebilirsiniz (kaynak kodda değiştirmek ve uygulamayı yeniden derlemek zorunda olmak yerine).

Hassas bilgilerin (parola gibi) bağlantı dizesi içinde depolanması, uygulamanın güvenliğini etkileyebilir. Uygulama yapılandırma dosyasına kaydedilen bağlantı dizeleri şifrelenmez veya karartılmalıdır. Bu nedenle, bir kullanıcının dosyaya erişmesi ve içeriğini görüntülemesi mümkün olabilir. Tümleşik Windows kullanarak veritabanına erişimi denetlemenin daha güvenli bir yolu vardır.

Windows tümleşik güvenliğini kullanmayı seçeseniz ve veritabanınız bir kullanıcı adı ve parola gerektiriyorsa, bunları bağlantı dizesinde atabilirsiniz, ancak veritabanına başarıyla bağlanmak için bu bilgileri uygulamanıza sağlamanız gerekir. Örneğin, kullanıcıdan bu bilgileri istenen ve çalışma zamanında bağlantı dizesini dinamik olarak oluşturan bir iletişim kutusu oluşturabilirsiniz. Bilgiler veritabanına doğru yolda kesişse de güvenlik sorunu devam ediyor olabilir.
Daha fazla bilgi için [bkz. Bağlantı bilgilerini koruma.](/dotnet/framework/data/adonet/protecting-connection-information)

## <a name="to-save-a-connection-string-from-within-the-data-source-configuration-wizard"></a>Bir bağlantı dizesini Veri Kaynağı Yapılandırma Sihirbazı'nın içinde kaydetmek için
Veri **Kaynağı Yapılandırma Sihirbazı'nda,** Bağlantı Dizesini Uygulama Yapılandırma Dosyasına Kaydet sayfasında **bağlantıyı kaydetme seçeneğini** belirleyin.

## <a name="to-save-a-connection-string-directly-into-application-settings"></a>Bağlantı dizesini doğrudan uygulama ayarlarına kaydetmek için
1. Bu **Çözüm Gezgini,** My **Project simgesine (Visual Basic)** veya **Özellikler** simgesine (C#) çift tıklar ve **Project Tasarımcısı'Project açın.**
1. **Ayarlar** sekmesini seçin.
1. Bağlantı dizesi **için** bir Ad girin. Kodda bağlantı dizesine erişirken bu adı kullanın.
1. Tür olarak **ayarlayın** (**Bağlantı dizesi**).
1. **Kapsam'ın Uygulama** olarak ayarlanmış şekilde **bırakın.**
1. Bağlantı dizenizi Değer **alanına** yazın veya Değer alanında üç nokta  **(...)** düğmesine  tıklayarak bağlantı dizenizi oluşturmak için Bağlantı Özellikleri iletişim kutusunu açın.

## <a name="edit-connection-strings-stored-in-application-settings"></a>Uygulama ayarlarında depolanan bağlantı dizelerini düzenleme
Uygulama ayarlarına kaydedilen bağlantı bilgilerini, Uygulama Tasarımcısı'Project **değiştirebilirsiniz.**

### <a name="to-edit-a-connection-string-stored-in-application-settings"></a>Uygulama ayarlarında depolanan bir bağlantı dizesini düzenlemek için
1. Bu **Çözüm Gezgini,** My **Project simgesine (Visual Basic)** veya **Özellikler** simgesine (C#) çift tıklar ve **Project Tasarımcısı'Project açın.**
1. **Ayarlar** sekmesini seçin.
1. Düzenlemek istediğiniz bağlantıyı bulun ve Değer alanında **metni** seçin.
1. Değer alanında bağlantı **dizesini** düzenleyin veya Bağlantı Özellikleri **iletişim** kutusuyla bağlantınızı düzenlemek için Değer alanında üç nokta (...)  **düğmesine** tıklayın.

## <a name="edit-connection-strings-for-datasets"></a>Veri kümeleri için bağlantı dizelerini düzenleme
Bir veri kümesinde her TableAdapter için bağlantı bilgilerini değiştirebilirsiniz.

### <a name="to-edit-a-connection-string-for-a-tableadapter-in-a-dataset"></a>Bir veri kümesinde TableAdapter için bağlantı dizesini düzenlemek için
1. Bu **Çözüm Gezgini,** düzenlemek istediğiniz bağlantının olduğu veri kümesine (**.xsd** dosyası) çift tıklayın.
1. Düzenlemek **istediğiniz bağlantının olduğu TableAdapter** veya sorguyu seçin.
1. Özellikler **penceresinde** Bağlantı düğümünü **genişletin.**
1. Bağlantı dizesini hızla değiştirmek için **ConnectionString** özelliğini düzenleyin veya Bağlantı özelliği üzerinde aşağı oka **tıklayın ve Yeni** Bağlantı'yı **seçin.**

## <a name="security"></a>Güvenlik
Hassas bilgilerin (parola gibi) bağlantı dizesi içinde depolanması, uygulamanın güvenliğini etkileyebilir. Tümleşik Windows kullanarak veritabanına erişimi denetlemenin daha güvenli bir yolu vardır.
Daha fazla bilgi için [bkz. Bağlantı bilgilerini koruma.](/dotnet/framework/data/adonet/protecting-connection-information)

## <a name="see-also"></a>Ayrıca bkz.

- [Bağlantı ekleme](../data-tools/add-new-connections.md)
