## Introduction ##
- A JSP Fragment Module to override the Web Content Articles Grid screen and the Web Content Articles Search Results grid screen to hide the Description and Path columns to prevent the need to scroll to see the item Actions.
  - The JSP to render this particular grid screen is: journal-web\src\main\resources\META-INF\resources\view_entries.jsp from module com.liferay.journal.web.jar in osgi/portal.
  - The only configuration to change the grid behavior is:
    - Switching the 'Display Style' in the GUI:
      - Cards label == displayStyle icon
      - Lists label == displayStyle descriptive
      - Table label == displayStyle list
    - Widget > Options > Configuration > Highlighted Structures which arguably makes it worse...
    - System Settings > Web Content > Administration to toggle the ID column which is hidden by default so no use here.
- The module is targeted at 2025.Q1.20
  - Fragment-Host: com.liferay.journal.web;bundle-version="5.0.185"
- The settings.gradle com.liferay.gradle.plugins.workspace should be set to "13.0.0" OR "latest.release"
  - There is a known issue with SOME recent workspace versions and jakarta dependency handling for JSP Fragment modules, whereby jakarta import package references are incorrectly included in place of javax in the JSP Fragment module MANIFEST.MF for pre-Jakarta Liferay versions.
- That the JSP Fragment modules JSPs should be 'rebased' as part of any future Liferay DXP upgrade.

## TODO ##
- Update the JSP based on the the columns to be hidden. For example:
  - It may be desirable to show the Path column in Search Results only.
  - Author column may not be relevant.
  - One or more of the Date columns (Modified Date / Display Date	/ Create Date) may not be relevant.
