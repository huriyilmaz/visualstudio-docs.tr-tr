---
title: Office çözümü için yapılandırma bilgilerini ayarlama
description: Microsoft Office çözümlerinize özgü ayarları yapılandırmak için yapılandırma dosyalarını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], configuration files
- configuration files [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: da3a08ad9b3f6c78a10891e7d8ef2093ab46305d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927710"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Nasıl yapılır: bir Office çözümü için yapılandırma bilgilerini ayarlama
  Yapılandırma dosyalarını, Office çözümlerinize özgü ayarları yapılandırmak için kullanabilirsiniz. Derleme bağlama ilkesi, uzaktan iletişim nesneleri, hata ayıklama ve izleme ayarları gibi ayarları belirtebilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Office projenize bir yapılandırma dosyası eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle**' ye tıklayın.

2. **Kategoriler** bölmesinde, **genel**' e tıklayın.

3. **Şablonlar** bölmesinde, **uygulama yapılandırma dosyası**' nı seçin.

4. **Ad** kutusuna derleme ile aynı adı ve *. config* uzantısını yazın. Örneğin, *ExcelWorkbook1.dll* adlı bir Excel projesi derlemesinin yapılandırma dosyası *ExcelWorkbook1.dll.config* olarak adlandırılır.

5. **Ekle**'ye tıklayın.

6. Yapılandırma dosyanızı uygulama yapılandırma dosyası şemasına göre oluşturun. Daha fazla bilgi için bkz. [.NET Framework Için yapılandırma dosyası şeması](/dotnet/framework/configure-apps/file-schema/index).

   Office projeleriyle yapılandırma dosyalarını kullanmaya yönelik özel önemli noktalar yoktur.

## <a name="see-also"></a>Ayrıca bkz.
- [.NET Framework için yapılandırma dosyası şeması](/dotnet/framework/configure-apps/file-schema/index)
- [Office çözümleri tasarlama ve oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md)
