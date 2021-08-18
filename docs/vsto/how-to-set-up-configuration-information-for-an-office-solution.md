---
title: Bir çözüm için yapılandırma bilgilerini Office ayarlama
description: Uygulama çözümlerinize özgü ayarları yapılandırmak için yapılandırma dosyalarını nasıl kullanabileceğinizi Microsoft Office öğrenin.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 1fd59fb61cf1d84c35bbcbbe406030318b8f57c6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032712"
---
# <a name="how-to-set-up-configuration-information-for-an-office-solution"></a>Nasıl Office: Bir Office ayarlama
  Yapılandırma dosyalarını kullanarak uygulama çözümlerinize özgü ayarları Office. Derleme bağlama ilkesi, iletişim nesneleri, hata ayıklama ve izleme ayarları gibi ayarları belirtebilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

### <a name="to-add-a-configuration-file-to-your-office-project"></a>Office projenize yapılandırma dosyası eklemek için

1. Yeni **Project** Ekle'ye **tıklayın.**

2. Kategoriler bölmesinde **Genel'e** **tıklayın.**

3. Şablonlar **bölmesinde Uygulama** Yapılandırma **Dosyası'ı seçin.**

4. Ad **kutusuna** derlemeyle aynı adı ve uzantıyı *.config.* Örneğin,ExcelWorkbook1.dlladlı bir Excel proje *derlemesi için yapılandırmaExcelWorkbook1.dll.config.* **

5. **Ekle**'ye tıklayın.

6. Yapılandırma dosyanızı uygulama yapılandırma dosyası şemasına göre oluşturun. Daha fazla bilgi için [bkz. Yapılandırma dosyası şeması .NET Framework.](/dotnet/framework/configure-apps/file-schema/index)

   Yapılandırma dosyalarını farklı projelerle kullanmanın özel bir Office yoktur.

## <a name="see-also"></a>Ayrıca bkz.
- [Yapılandırma dosyası şeması .NET Framework](/dotnet/framework/configure-apps/file-schema/index)
- [Yeni çözümler tasarlama Office oluşturma](../vsto/designing-and-creating-office-solutions.md)
- [Bir Office dağıtma](../vsto/deploying-an-office-solution.md)
