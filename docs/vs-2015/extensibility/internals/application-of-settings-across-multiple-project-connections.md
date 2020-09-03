---
title: Birden çok proje bağlantısı arasında ayarların uygulaması | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bca17fdc440fc373d0d4811ed57cd5d27a6c201a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203853"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Birden Çok Proje Bağlantısında Ayarların Uygulanması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi eklentisi API 1,2 kullanılarak oluşturulan bir kaynak denetimi eklentisi, birden fazla proje veya birden çok bağlantı bağlamı genelinde aynı kaynak denetimi işlemini yürütmek için bir toplu işlem kullanabilir. Toplu işler, Kullanıcı deneyiminden proje başına gereksiz iletişim kutularını ortadan kaldırmak için kullanılabilir.  
  
 Bir Kullanıcı, kaynak denetimi eklentisi API 1,1 (örneğin, farklı dosya paylaşma makinelerinde iki Web projesi) kullanılarak oluşturulmuş bir kaynak denetim eklentisinde birden fazla bağlantıya ait birden çok öğe seçerse ve bunları denetlerse, Kullanıcı aynı iletişim kutusunu sürekli olarak görür. Bu durum, IDE, her bağlantı bağlamı için durumunu sıfırladığında, Kullanıcı iletişim kutusundaki **Tümüne Uygula** onay kutusuna tıklasa bile gerçekleşir.  
  
## <a name="new-capability-flag"></a>Yeni yetenek bayrağı  
 `SccBeginBatch` Function `SCC_CAP_BATCH` bir toplu işlemin devam ettiğini belirten bayrağı ayarlar  
  
## <a name="new-functions"></a>Yeni Işlevler  
 Aşağıdaki yeni işlevler Batch işlemini destekler:  
  
- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)  
  
- [SccEndBatch](../../extensibility/sccendbatch-function.md)  
  
  `SCCBeginBatch`İşlevi, kaynak denetimi işlemleri grubunu başlatır. `SccEndBatch` grubu kapatır. Gruplar iç içe olamaz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
