# SoOoMa TV Public EPG Test Fixtures

These fixtures are synthetic test data for diagnosing external XMLTV guide integration in SoOoMa TV. They contain no customer or IPTV subscription information, and are not real broadcast programme listings.

- M3U playlist: https://raw.githubusercontent.com/SeMoOo/SoOoMa-TV-Support/main/epg-test/sample.m3u
- M3U XMLTV: https://raw.githubusercontent.com/SeMoOo/SoOoMa-TV-Support/main/epg-test/sample.xml
- Xtream demo external XMLTV: https://raw.githubusercontent.com/SeMoOo/SoOoMa-TV-Support/main/epg-test/xtream-override.xml

The Xtream XMLTV file is designed for the public `demo / demo` mock Xtream API at `https://api-tester-fcn5.onrender.com`, not arbitrary providers.

In Web Manager, save one of the XMLTV links as the EPG URL for the matching account and then use **Test EPG**. A matching result verifies download, XML parsing and at least one channel match.

Schedules cover October 8 through November 21, 2026 UTC. These examples are unsuitable as a long-lived production EPG source. Never place private playlists, tokens or subscriber credentials in this public folder.
