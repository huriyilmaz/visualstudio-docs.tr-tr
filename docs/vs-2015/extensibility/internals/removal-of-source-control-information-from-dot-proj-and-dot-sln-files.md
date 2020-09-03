---
title: Kaynak denetim bilgilerinin konumundan kaldırılması. PROJ ve. Sln dosyaları | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, .sln and .proj files
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b7cdaeb02f77d3775096f840a513f68e531b1299
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199382"
---
# <a name="removal-of-source-control-information-from-proj-and-sln-files"></a>.Proj ve .Sln Dosyalarından Kaynak Denetimi Bilgilerinin Kaldırılması
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kaynak denetimi eklentisi API 'sinin sürüm 1,2 ' de, SCC bilgileri bir MSSCCPRJ depolanır. SCC dosyası. MSSCCPRJ avantajı. SCC dosyası. proj ve. sln dosyalarında olduğu gibi, SCC bilgisinin kaynak denetimli olmaması olabilir.  
  
## <a name="version-12-changes"></a>Sürüm 1,2 değişiklikleri  
 Kaynak denetimi eklentisi API sürüm 1,1 ' i temel alan kaynak denetimi eklentilerinde, kaynak denetimi ile ilgili bilgiler proje (. proj) ve çözüm (. sln) dosyalarında depolanır. Kaynak denetim bilgisinin veritabanı konumu AuxPath tarafından belirtilir ve veritabanı içindeki belirli konum ProjName tarafından belirtilir. Bu davranış, bu işlemlerden herhangi biri sonrasında ProjName genellikle geçersiz olacağından, dal, çatal veya kopyalama işlemlerinden sonra sorunlara yol açabilir.  
  
 Kaynak denetimi eklentisi API sürümü 1,1 ' de, IDE, bir eklentinin MSSCCPRJ tarafından desteklenip desteklenmediğini algılamak için ~ SAK dosyalarını kullandı. Kaynak denetim bilgilerini depolamanın SCC yöntemi. Kaynak denetimi eklentisi API sürümü 1,2, MSSCCPRJ desteğini algılamaya yönelik yeni bir özellik sunar. Bir ~ SAK dosyası kullanmadan SCC dosyası. Daha fazla bilgi için bkz. yok [~ sak Files](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak Denetimi Eklentisi API Sürümü 1.2’deki Yenilikler](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
