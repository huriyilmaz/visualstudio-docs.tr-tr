---
title: SharePoint çözümleri oluşturma ve hata ayıklama | Microsoft Docs
description: SharePoint çözümleri oluşturup hata ayıklamanın yanı sıra Visual Studio diğer proje türlerini oluşturma ve hata ayıklamanın nasıl farklı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, building and debugging
- SharePoint development in Visual Studio, debugging
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 8da574fb42e9a34bef81bd6690861141cfeec941
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027220"
---
# <a name="build-and-debug-sharepoint-solutions"></a>SharePoint çözümleri oluşturun ve hata ayıklayın
  genel olarak, SharePoint çözümleri derleme ve hata ayıklama, içindeki diğer proje türlerini derleme ve hata ayıklama ile aynıdır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Bu bölümdeki konular, var olan farkları açıklamaktadır.

## <a name="project-output-for-sharepoint-solutions"></a>SharePoint çözümleri için çıkış Project
 SharePoint çözümlerin oluşturulması, derlemeler ve bir çözüm paketi (*. wsp*) dosyası oluşturur. Aşağıdaki tabloda, bir derleme sırasında bu dosyaların konumları gösterilmektedir.

|Derleme öğesi|Çıkış klasörü|
|----------------|-------------------|
|Derleme, program veritabanı (*. pdb*) ve *. wsp* dosyaları.|*\<ProjectName> \Bin\Debug* veya *\<ProjectName> \bin\Release*|
|proje öğesi dosyalarını SharePoint.|*\<ProjectName> \pkg\debug* veya *\<ProjectName> \pkg\release*|
|Ara dosyalar oluşturun.|*\<ProjectName> \obj\debug* veya *\<ProjectName> \obj\release*|
|Paket ara dosyaları.|*\<ProjectName> \pkgobj\debug* veya *\<ProjectName> \pkgobj\release*|

## <a name="build-sharepoint-solutions"></a>SharePoint çözümleri oluşturun
 SharePoint çözümleri derlemek için geliştirme bilgisayarında doğru SharePoint server sürümü yüklü olmalıdır. aksi takdirde, SharePoint çözümlerin oluşturulması ' de diğer proje türlerini oluşturma ile aynıdır [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . daha fazla bilgi için bkz. [nasıl yapılır: derleme SharePoint çözümleri](../sharepoint/how-to-build-sharepoint-solutions.md).

## <a name="debug-and-test-sharepoint-solutions"></a>hata ayıklama ve test SharePoint çözümleri
 hata ayıklamadan önce, [!include[vsprvs](../sharepoint/includes/vsprvs-md.md)] *. wsp* paketini SharePoint sunucusuna kopyalar, siteyi ve Web kapsamlı özellikleri etkinleştirir ve bazı durumlarda projeyi başlatır. Diğer durumlarda, projeyi el ile açmanız gerekebilir. daha fazla bilgi için bkz. [sorun giderme SharePoint çözümleri](../sharepoint/troubleshooting-sharepoint-solutions.md) ve [hata ayıklama SharePoint çözümleri](../sharepoint/debugging-sharepoint-solutions.md).

## <a name="debug-and-verify-sharepoint-solutions-by-using-azure-devops-services-features"></a>Azure DevOps Services özelliklerini kullanarak hata ayıklama ve SharePoint çözümleri doğrulama
 birim testi ve ıntellitrace gibi Azure DevOps Services özellikler, SharePoint çözümlerinizde sorunları daha doğru bir şekilde belirlemenize olanak sağlar. profil oluşturma, SharePoint çözümlerinizde performans sorunu alanını bulmanıza ve tanımlamanızı sağlar. daha fazla bilgi için bkz. [SharePoint kodu doğrulama ve hata ayıklama](../sharepoint/verifying-and-debugging-sharepoint-code.md) ve [SharePoint uygulamaların performansını profil oluşturma](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).

## <a name="security-during-the-build-process"></a>Oluşturma işlemi sırasında güvenlik
 SharePoint çözümlerini paketlemek veya dağıtmak için, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] dosyaları SharePoint sunucusuna kopyalamak için izninizin olması gerekir. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]yükseltilmiş bir işlem olarak çalıştırmalısınız ve kullanıcı hesabınızın SharePoint sunucuda bir Site koleksiyonları yöneticisi olması gerekir. Ayrıca, projenizin korumalı bir çözüm mi yoksa Grup çözümü mi olduğunu belirtmeniz gerekir. Daha fazla bilgi için bkz. [korumalı ve Grup çözümleri arasındaki farklılıklar](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).

## <a name="using-the-clean-command"></a>Clean komutunu kullanma
 hata ayıklama için bir SharePoint sunucusuna SharePoint çözümü yüklendiğinde, **temizleme** komutu çözümü kaldırmaz. bunun yerine, SharePoint yapılandırması aracılığıyla özellikleri devre dışı bırakmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)
- [Sunucu Gezgini kullanarak SharePoint bağlantılara gözatamazsınız](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)
- [SharePoint çözümleri paketleme ve dağıtma](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)
