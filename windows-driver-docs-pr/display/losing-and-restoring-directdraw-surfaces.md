---
title: Losing and Restoring DirectDraw Surfaces
description: Losing and Restoring DirectDraw Surfaces
ms.assetid: 74203932-8a30-44ea-8d0d-45265dd2e74a
keywords:
- drawing surfaces WDK DirectDraw , losing
- DirectDraw surfaces WDK Windows 2000 display , losing
- surfaces WDK DirectDraw , losing
- drawing surfaces WDK DirectDraw , restoring
- DirectDraw surfaces WDK Windows 2000 display , restoring
- surfaces WDK DirectDraw , restoring
- restoring surfaces WDK DirectDraw
- lost surfaces WDK DirectDraw
- suspended surfaces WDK DirectDraw
ms.date: 04/20/2017
ms.localizationpriority: medium
---

# Losing and Restoring DirectDraw Surfaces


## <span id="ddk_losing_and_restoring_directdraw_surfaces_gg"></span><span id="DDK_LOSING_AND_RESTORING_DIRECTDRAW_SURFACES_GG"></span>


Surface object lifetimes are longer for the runtime's surface objects than they are for the driver's surface objects. In a few situations, most notably mode changes, surfaces become *lost*. This means that the driver's surface object is destroyed when [*DdDestroySurface*](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_surfcb_destroysurface) is called, but the runtime's surface object is placed into a suspended state. Later, the runtime object can be *restored*, which corresponds to a [*DdCreateSurface*](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff549263(v=vs.85)) call at the driver level.

Normally, drivers do not have to be aware of this intermediate lost state. However, there are some cases where an understanding of this process will help the driver writer.

Driver writers can elect to handle complex surface restoration in one atomic call. At surface restoration time, the DirectDraw runtime examines the driver's [**D3dCreateSurfaceEx**](https://docs.microsoft.com/windows/desktop/api/ddrawint/nc-ddrawint-pdd_createsurfaceex) entry point. If this entry point is defined, then the DirectDraw runtime restores all complex surfaces in one call to [*DdCreateSurface*](https://docs.microsoft.com/previous-versions/windows/hardware/drivers/ff549263(v=vs.85)). The driver probably will not be able to differentiate between the original creation and the creation caused by restoring a surface.

 

 





