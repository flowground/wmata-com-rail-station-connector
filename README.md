# ![LOGO](logo.png) Rail Station Information **flow**ground Connector

## Description

A generated **flow**ground connector for the Rail Station Information API (version 1.0).

Generated from: https://api.apis.guru/v2/specs/wmata.com/rail-station/1.0/swagger.json<br/>
Generated at: 2019-05-07T17:45:00+03:00

## API Description

Rail line and station information, including locations, fares, times, and parking.

## Authorization

Supported authorization schemes:
- API Key- API Key
## Actions

### XML - Lines

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns information about all rail lines.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Lines</td>
> 
> <td>
> Array containing line information (<a href="#Line">Line</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="Line" name="Line">Line Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>DisplayName</td>
> 
> <td>Full name of line color.</td>
> </tr>
> 
> <tr>
> <td>EndStationCode</td>
> 
> <td>End station code. For example, will be E10 (Greenbelt) for the
> Green Line, B11 (Glenmont) for the Red Line, etc. Use this value in
> other rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>InternalDestination1</td>
> 
> <td>Intermediate terminal station code. During normal service, some
> trains on some lines might end their trip prior to the
> StartStationCode or EndStationCode. A good example is on the Red
> Line where some trains stop at A11 (Grosvenor) or B08 (Silver
> Spring). Empty string if not defined.</td>
> </tr>
> 
> <tr>
> <td>InternalDestination2</td>
> 
> <td>Similar to InternalDestination1.</td>
> </tr>
> 
> <tr>
> <td>LineCode</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV).</td>
> </tr>
> 
> <tr>
> <td>StartStationCode</td>
> 
> <td>Start station code. For example, will be F11 (Branch Avenue)
> for the Green Line, A15 (Shady Grove) for the Red Line, etc. Use
> this value in other rail-related APIs to retrieve data about a
> station.</td>
> </tr>
> </tbody>
> </table>

### XML - Path Between Stations

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns a set of ordered stations and distances between two stations on the
> <em>same line</em>.</p>
> 
> <p>Note that this method is not suitable on its own as a pathfinding solution
> between stations.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Path</td>
> 
> <td>
> Array containing path details (<a href=
> "#MetroPathItem">MetroPathItem</a>)
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="MetroPathItem" name="MetroPathItem">MetroPathItem
> Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>DistanceToPrev</td>
> 
> <td>Distance in feet to the previous station in the list.</td>
> </tr>
> 
> <tr>
> <td>LineCode</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV) this station's platform is on.</td>
> </tr>
> 
> <tr>
> <td>SeqNum</td>
> 
> <td>Ordered sequence number.</td>
> </tr>
> 
> <tr>
> <td>StationCode</td>
> 
> <td>Station code for this station. Use this value in other
> rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>StationName</td>
> 
> <td>Full name for this station, as shown on the WMATA website.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `FromStationCode` - _required_ - Station code for the origin station.  Use the Station List method to return a list of all station codes.
    Possible values: N06.
* `ToStationCode` - _required_ - Station code for the origin station.  Use the Station List method to return a list of all station codes.
    Possible values: G05.

### XML - Station to Station Information

> <h4 class="text-primary">Description</h4><br/>
> <br/>
> <p>Returns a distance, fare information, and estimated travel time between any<br/>
> two stations, including those on different lines. Omit both parameters to<br/>
> retrieve data for all stations.</p><br/>
> <br/>
> <h4 class="text-primary">Response Elements</h4><br/>
> <br/>
> <table class="table table-condensed table-hover"><br/>
> <thead><br/>
> <tr><br/>
> <th class="col-md-3">Element</th><br/>
> <br/>
> <th>Description</th><br/>
> </tr><br/>
> </thead><br/>
> <br/>
> <tbody><br/>
> <tr><br/>
> <td>StationToStationInfos</td><br/>
> <br/>
> <td><br/>
> Array containing station to station information (<a href=<br/>
> "#StationToStationInfo">StationToStationInfo</a>).<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="StationToStationInfo" name=<br/>
> "StationToStationInfo">StationToStationInfo Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>CompositeMiles</td><br/>
> <br/>
> <td>Average of distance traveled between two stations and straight-line distance (as used for WMATA fare calculations).  For more details, please refer to WMATA's <a href="https://www.wmata.com/about/records/public_docs/upload/Tariff-on-Fares-Annotated-2-12-18.pdf#page=6" target="_blank" rel="noopener noreferrer">Tariff on Fares</a>.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>DestinationStation</td><br/>
> <br/>
> <td>Destination station code. Use this value in other rail-related<br/>
> APIs to retrieve data about a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>RailFare</td><br/>
> <br/>
> <td><br/>
> Structure containing <a href="#RailFare">fare</a> information.<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>RailTime</td><br/>
> <br/>
> <td>Estimated travel time (schedule time) in minutes between the source and<br/>
> destination station. This is not correlated to minutes <span class="text-info">(Min)</span> in Real-Time Rail Predictions.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SourceStation</td><br/>
> <br/>
> <td>Origin station code. Use this value in other rail-related APIs<br/>
> to retrieve data about a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="RailFare" name="RailFare">RailFare Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>OffPeakTime</td><br/>
> <br/>
> <td>Fare during off-peak times (times other than the ones described<br/>
> below).</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>PeakTime</td><br/>
> <br/>
> <td>Fare during peak times (weekdays from opening to 9:30 AM and<br/>
> 3-7 PM, and weekends from midnight to closing).</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SeniorDisabled</td><br/>
> <br/>
> <td><br/>
> Reduced fare for <a href=<br/>
> "http://www.wmata.com/fares/reduced.cfm">senior citizens or<br/>
> people with disabilities</a>.<br/>
> </td><br/>
> </tr><br/>
> </tbody><br/>
> </table>

#### Input Parameters
* `FromStationCode` - _optional_ - Station code for the origin station.  Use the Station List method to return a list of all station codes.
    Possible values: E10.
* `ToStationCode` - _optional_ - Station code for the destination station.  Use the Station List method to return a list of all station codes.
    Possible values: J03.

### XML - Station Entrances

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns a list of nearby station entrances based on latitude, longitude, and
> radius (meters). Omit search parameters to return all station entrances.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Entrances</td>
> 
> <td>
> Array containing detailed information about station entrances
> (<a href="#StationEntrance">StationEntrance</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="StationEntrance" name=
> "StationEntrance">StationEntrance Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Description</td>
> 
> <td>Additional information for the entrance, if available.
> Currently available data usually shows the same value as the Name
> element.</td>
> </tr>
> 
> <tr>
> <td style="text-decoration: line-through">ID</td>
> 
> <td><span class="text-danger">Deprecated.</span></td>
> </tr>
> 
> <tr>
> <td>Lat</td>
> 
> <td>Latitude.</td>
> </tr>
> 
> <tr>
> <td>Lon</td>
> 
> <td>Longitude.</td>
> </tr>
> 
> <tr>
> <td>Name</td>
> 
> <td>Name of the entrance (usually the station name and nearest
> intersection).</td>
> </tr>
> 
> <tr>
> <td>StationCode1</td>
> 
> <td>The station code associated with this entrance. Use this value
> in other rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>StationCode2</td>
> 
> <td>For stations containing multiple platforms (e.g.: Gallery
> Place, Fort Totten, L'Enfant Plaza, and Metro Center), the other
> station code.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `Lat` - _optional_ - Center point Latitude, required if Longitude and Radius are specified.
    Possible values: 38.8978168.
* `Lon` - _optional_ - Center point Longitude, required if Latitude and Radius are specified.
    Possible values: -77.0404246.
* `Radius` - _optional_ - Radius (meters) to include in the search area, required if Latitude and Longitude are specified.
    Possible values: 500.

### XML - Station Information

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns station location and address information based on a given
> StationCode.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Address</td>
> 
> <td>
> Structure describing <a href="#Address">address</a> information.
> </td>
> </tr>
> 
> <tr>
> <td>Code</td>
> 
> <td>Station code. Repeated from input.</td>
> </tr>
> 
> <tr>
> <td>Lat</td>
> 
> <td>Latitude.</td>
> </tr>
> 
> <tr>
> <td>LineCode1</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV) served by this station.</td>
> </tr>
> 
> <tr>
> <td>LineCode2</td>
> 
> <td>Additional line served by this station. This is often the case
> when stations have multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center).</td>
> </tr>
> 
> <tr>
> <td>LineCode3</td>
> 
> <td>Similar to function as LineCodeX.</td>
> </tr>
> 
> <tr>
> <td>LineCode4</td>
> 
> <td>Similar to function as LineCodeX. Currently not in use.</td>
> </tr>
> 
> <tr>
> <td>Lon</td>
> 
> <td>Longitude.</td>
> </tr>
> 
> <tr>
> <td>Name</td>
> 
> <td>Station name.</td>
> </tr>
> 
> <tr>
> <td>StationTogether1</td>
> 
> <td>For stations with multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center), the additional
> StationCode will be listed here.</td>
> </tr>
> 
> <tr>
> <td>StationTogether2</td>
> 
> <td>Similar in function to StationTogether2. Currently not in
> use.</td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a name="Address">Address Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>City</td>
> 
> <td>City.</td>
> </tr>
> 
> <tr>
> <td>State</td>
> 
> <td>State (abbreviated).</td>
> </tr>
> 
> <tr>
> <td>Street</td>
> 
> <td>Street address (for GPS use).</td>
> </tr>
> 
> <tr>
> <td>Zip</td>
> 
> <td>Zip code.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `StationCode` - _required_ - Station code.  Use the Station List method to return a list of all station codes.
    Possible values: A01.

### XML - Parking Information

> <h4 class="text-primary">Description</h4><br/>
> <br/>
> <p>Returns parking information at a station based on a given StationCode. Omit<br/>
> the StationCode to return parking information for all stations.</p><br/>
> <br/>
> <p>If a station has no parking, the StationsParking element will contain no<br/>
> child elements.</p><br/>
> <br/>
> <h4 class="text-primary">Response Elements</h4><br/>
> <br/>
> <table class="table table-condensed table-hover"><br/>
> <thead><br/>
> <tr><br/>
> <th class="col-md-3">Element</th><br/>
> <br/>
> <th>Description</th><br/>
> </tr><br/>
> </thead><br/>
> <br/>
> <tbody><br/>
> <tr><br/>
> <td>StationsParking</td><br/>
> <br/>
> <td><br/>
> Array containing station parking information (<a href=<br/>
> "#StationParking">StationParking</a>).<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="StationParking" name="StationParking">StationParking<br/>
> Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>Code</td><br/>
> <br/>
> <td>Station code. Useful when returning parking information for all<br/>
> stations. Use this value in other rail-related APIs to retrieve<br/>
> data about a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>Notes</td><br/>
> <br/>
> <td>When not NULL, provides additional parking resources such as<br/>
> nearby lots.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>AllDayParking</td><br/>
> <br/>
> <td><br/>
> Structure describing <a href="#AllDayParking">all-day<br/>
> parking</a> options.<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>ShortTermParking</td><br/>
> <br/>
> <td><br/>
> Structure describing <a href="#ShortTermParking">short-term<br/>
> parking</a> options.<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="AllDayParking" name="AllDayParking">AllDayParking<br/>
> Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>TotalCount</td><br/>
> <br/>
> <td>Number of all-day parking spots available at a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>RiderCost</td><br/>
> <br/>
> <td>All-day cost per day (weekday) for Metro riders. NULL when no all-day<br/>
> spots are available. For most stations, this value is identical to<br/>
> the NonRiderCost.<br><br/>
> <br><br/>
> For cases where the NonRiderCost is different, the lower cost per<br/>
> day requires a valid rail trip using a SmarTrip&reg; card<br/>
> originating from a station other than the one where the patron<br/>
> parked. To receive this lower rate, patrons must pay for their<br/>
> parking with the same SmarTrip&reg; card used to enter/exit<br/>
> Metrorail, and must exit the parking lot within two hours of<br/>
> exiting Metrorail.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>NonRiderCost</td><br/>
> <br/>
> <td>All-day cost per day (weekday) for non-Metro riders. NULL when no all-day<br/>
> spots are available.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="ShortTermParking" name=<br/>
> "ShortTermParking">ShortTermParking Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SaturdayRiderCost</td><br/>
> <br/>
> <td>Similar to RiderCost, except denoting Saturday prices.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SaturdayNonRiderCost</td><br/>
> <br/>
> <td>Similar to NonRiderCost, except denoting Saturday prices.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>TotalCount</td><br/>
> <br/>
> <td>Number of short-term parking spots available at a station<br/>
> (parking meters).</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>Notes</td><br/>
> <br/>
> <td>Misc. information relating to short-term parking. NULL when no<br/>
> short-term spots are available.</td><br/>
> </tr><br/>
> </tbody><br/>
> </table>

#### Input Parameters
* `StationCode` - _optional_ - Station code.  Use the Station List method to return a list of all station codes.
    Possible values: E08, F06.

### XML - Station Timings

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns opening and scheduled first/last train times based on a given
> StationCode. Omit the StationCode to return timing information for all
> stations.</p>
> 
> <p>Note that for stations with multiple platforms (e.g.: Metro Center, L'Enfant
> Plaza, etc.), a distinct call is required for each StationCode to retrieve the
> full set of train times at such stations.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>StationTimes</td>
> 
> <td>
> Array containing station timing information (<a href=
> "#StationTime">StationTime</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="StationTime" name="StationTime">StationTime
> Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Code</td>
> 
> <td>Station code for this station. Use this value in other
> rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>StationName</td>
> 
> <td>Full name of the station.</td>
> </tr>
> 
> <tr>
> <td>*Day Elements</td>
> 
> <td>
> Container elements containing timing information based on
> <a href="#dow">day of the week.</a>
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="dow" name="dow">Monday/Tuesday/Wednesday/etc.
> Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>OpeningTime</td>
> 
> <td>Station opening time. Format is HH:mm.</td>
> </tr>
> 
> <tr>
> <td>FirstTrains</td>
> 
> <td>
> Structure containing <a href="#first">first train</a>
> information.
> </td>
> </tr>
> 
> <tr>
> <td>LastTrains</td>
> 
> <td>
> Structure containing <a href="#last">last train</a>
> information.
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="first" name="first">FirstTrains Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Time</td>
> 
> <td>First train leaves the station at this time. Format is
> HH:mm.</td>
> </tr>
> 
> <tr>
> <td>DestinationStation</td>
> 
> <td>Station code for the train's destination. Use this value in
> other rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="last" name="last">LastTrains Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Time</td>
> 
> <td>Last train leaves the station at this time. Format is HH:mm.
> Note that when the time is AM, it signifies the next day. For
> example, a value of 02:30 under a Saturday element means the last
> train leaves on Sunday at 2:30 AM.</td>
> </tr>
> 
> <tr>
> <td>DestinationStation</td>
> 
> <td>Station code for the train's destination. Use this value in
> other rail-related APIs to retrieve data about a station.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `StationCode` - _optional_ - Station code.  Use the Station List method to return a list of all station codes.
    Possible values: E10.

### XML - Station List

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns a list of station location and address information based on a given
> LineCode. Omit the LineCode to return all stations. The response is an array of
> objects identical to those returned in the Station Information method.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Stations</td>
> 
> <td>
> Array containing station information (<a href=
> "#Station">Station</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="Station" name="Station">Station Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Address</td>
> 
> <td>
> Structure describing <a href="#Address">address</a> information.
> </td>
> </tr>
> 
> <tr>
> <td>Code</td>
> 
> <td>Station code. Repeated from input.</td>
> </tr>
> 
> <tr>
> <td>Lat</td>
> 
> <td>Latitude.</td>
> </tr>
> 
> <tr>
> <td>LineCode1</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV) served by this station.</td>
> </tr>
> 
> <tr>
> <td>LineCode2</td>
> 
> <td>Additional line served by this station. This is often the case
> when stations have multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center).</td>
> </tr>
> 
> <tr>
> <td>LineCode3</td>
> 
> <td>Similar to function as LineCodeX.</td>
> </tr>
> 
> <tr>
> <td>LineCode4</td>
> 
> <td>Similar to function as LineCodeX. Currently not in use.</td>
> </tr>
> 
> <tr>
> <td>Lon</td>
> 
> <td>Longitude.</td>
> </tr>
> 
> <tr>
> <td>Name</td>
> 
> <td>Station name.</td>
> </tr>
> 
> <tr>
> <td>StationTogether1</td>
> 
> <td>For stations with multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center), the additional
> StationCode will be listed here.</td>
> </tr>
> 
> <tr>
> <td>StationTogether2</td>
> 
> <td>Similar in function to StationTogether2. Currently not in
> use.</td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="Address" name="Address">Address Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>City</td>
> 
> <td>City.</td>
> </tr>
> 
> <tr>
> <td>State</td>
> 
> <td>State (abbreviated).</td>
> </tr>
> 
> <tr>
> <td>Street</td>
> 
> <td>Street address (for GPS use).</td>
> </tr>
> 
> <tr>
> <td>Zip</td>
> 
> <td>Zip code.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `LineCode` - _optional_ - Two-letter line code abbreviation:

<ul>
<li>RD - Red</li>
<li>YL - Yellow</li>
<li>GR - Green</li>
<li>BL - Blue</li>
<li>OR - Orange</li>
<li>SV - Silver</li>
</ul>
    Possible values: RD, YL, GR, BL, OR, SV.

### JSON - Lines

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns information about all rail lines.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Lines</td>
> 
> <td>
> Array containing line information (<a href="#Line">Line</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="Line" name="Line">Line Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>DisplayName</td>
> 
> <td>Full name of line color.</td>
> </tr>
> 
> <tr>
> <td>EndStationCode</td>
> 
> <td>End station code. For example, will be E10 (Greenbelt) for the
> Green Line, B11 (Glenmont) for the Red Line, etc. Use this value in
> other rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>InternalDestination1</td>
> 
> <td>Intermediate terminal station code. During normal service, some
> trains on some lines might end their trip prior to the
> StartStationCode or EndStationCode. A good example is on the Red
> Line where some trains stop at A11 (Grosvenor) or B08 (Silver
> Spring). Empty string if not defined.</td>
> </tr>
> 
> <tr>
> <td>InternalDestination2</td>
> 
> <td>Similar to InternalDestination1.</td>
> </tr>
> 
> <tr>
> <td>LineCode</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV).</td>
> </tr>
> 
> <tr>
> <td>StartStationCode</td>
> 
> <td>Start station code. For example, will be F11 (Branch Avenue)
> for the Green Line, A15 (Shady Grove) for the Red Line, etc. Use
> this value in other rail-related APIs to retrieve data about a
> station.</td>
> </tr>
> </tbody>
> </table>

### JSON - Path Between Stations

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns a set of ordered stations and distances between two stations on the
> <em>same line</em>.</p>
> 
> <p>Note that this method is not suitable on its own as a pathfinding solution
> between stations.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Path</td>
> 
> <td>
> Array containing path details (<a href=
> "#MetroPathItem">MetroPathItem</a>)
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="MetroPathItem" name="MetroPathItem">MetroPathItem
> Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>DistanceToPrev</td>
> 
> <td>Distance in feet to the previous station in the list.</td>
> </tr>
> 
> <tr>
> <td>LineCode</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV) this station's platform is on.</td>
> </tr>
> 
> <tr>
> <td>SeqNum</td>
> 
> <td>Ordered sequence number.</td>
> </tr>
> 
> <tr>
> <td>StationCode</td>
> 
> <td>Station code for this station. Use this value in other
> rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>StationName</td>
> 
> <td>Full name for this station, as shown on the WMATA website.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `FromStationCode` - _required_ - Station code for the origin station.  Use the Station List method to return a list of all station codes.
    Possible values: N06.
* `ToStationCode` - _required_ - Station code for the destination station.  Use the Station List method to return a list of all station codes.
    Possible values: G05.

### JSON - Station to Station Information

> <h4 class="text-primary">Description</h4><br/>
> <br/>
> <p>Returns a distance, fare information, and estimated travel time between any<br/>
> two stations, including those on different lines. Omit both parameters to<br/>
> retrieve data for all stations.</p><br/>
> <br/>
> <h4 class="text-primary">Response Elements</h4><br/>
> <br/>
> <table class="table table-condensed table-hover"><br/>
> <thead><br/>
> <tr><br/>
> <th class="col-md-3">Element</th><br/>
> <br/>
> <th>Description</th><br/>
> </tr><br/>
> </thead><br/>
> <br/>
> <tbody><br/>
> <tr><br/>
> <td>StationToStationInfos</td><br/>
> <br/>
> <td><br/>
> Array containing station to station information (<a href=<br/>
> "#StationToStationInfo">StationToStationInfo</a>).<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="StationToStationInfo" name=<br/>
> "StationToStationInfo">StationToStationInfo Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>CompositeMiles</td><br/>
> <br/>
> <td>Average of distance traveled between two stations and straight-line distance (as used for WMATA fare calculations).  For more details, please refer to WMATA's <a href="https://www.wmata.com/about/records/public_docs/upload/Tariff-on-Fares-Annotated-2-12-18.pdf#page=6" target="_blank" rel="noopener noreferrer">Tariff on Fares</a>.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>DestinationStation</td><br/>
> <br/>
> <td>Destination station code. Use this value in other rail-related<br/>
> APIs to retrieve data about a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>RailFare</td><br/>
> <br/>
> <td><br/>
> Structure containing <a href="#RailFare">fare</a> information.<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>RailTime</td><br/>
> <br/>
> <td>Estimated travel time (schedule time) in minutes between the source and<br/>
> destination station. This is not correlated to minutes <span class="text-info">(Min)</span> in Real-Time Rail Predictions.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SourceStation</td><br/>
> <br/>
> <td>Origin station code. Use this value in other rail-related APIs<br/>
> to retrieve data about a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="RailFare" name="RailFare">RailFare Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>OffPeakTime</td><br/>
> <br/>
> <td>Fare during off-peak times (times other than the ones described<br/>
> below).</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>PeakTime</td><br/>
> <br/>
> <td>Fare during peak times (weekdays from opening to 9:30 AM and<br/>
> 3-7 PM, and weekends from midnight to closing).</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SeniorDisabled</td><br/>
> <br/>
> <td><br/>
> Reduced fare for <a href=<br/>
> "http://www.wmata.com/fares/reduced.cfm">senior citizens or<br/>
> people with disabilities</a>.<br/>
> </td><br/>
> </tr><br/>
> </tbody><br/>
> </table>

#### Input Parameters
* `FromStationCode` - _optional_ - Station code for the origin station.  Use the Station List method to return a list of all station codes.
    Possible values: E10.
* `ToStationCode` - _optional_ - Station code for the destination station.  Use the Station List method to return a list of all station codes.
    Possible values: J03.

### JSON - Station Entrances

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns a list of nearby station entrances based on latitude, longitude, and
> radius (meters). Omit search parameters to return all station entrances.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Entrances</td>
> 
> <td>
> Array containing detailed information about station entrances
> (<a href="#StationEntrance">StationEntrance</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="StationEntrance" name=
> "StationEntrance">StationEntrance Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Description</td>
> 
> <td>Additional information for the entrance, if available.
> Currently available data usually shows the same value as the Name
> element.</td>
> </tr>
> 
> <tr>
> <td style="text-decoration: line-through">ID</td>
> 
> <td><span class="text-danger">Deprecated.</span></td>
> </tr>
> 
> <tr>
> <td>Lat</td>
> 
> <td>Latitude.</td>
> </tr>
> 
> <tr>
> <td>Lon</td>
> 
> <td>Longitude.</td>
> </tr>
> 
> <tr>
> <td>Name</td>
> 
> <td>Name of the entrance (usually the station name and nearest
> intersection).</td>
> </tr>
> 
> <tr>
> <td>StationCode1</td>
> 
> <td>The station code associated with this entrance. Use this value
> in other rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>StationCode2</td>
> 
> <td>For stations containing multiple platforms (e.g.: Gallery
> Place, Fort Totten, L'Enfant Plaza, and Metro Center), the other
> station code.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `Lat` - _optional_ - Center point Latitude, required if Longitude and Radius are specified.
    Possible values: 38.8978168.
* `Lon` - _optional_ - Center point Longitude, required if Latitude and Radius are specified.
    Possible values: -77.0404246.
* `Radius` - _optional_ - Radius (meters) to include in the search area, required if Latitude and Longitude are specified.
    Possible values: 500.

### JSON - Station Information

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns station location and address information based on a given
> StationCode.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Address</td>
> 
> <td>
> Structure describing <a href="#Address">address</a> information.
> </td>
> </tr>
> 
> <tr>
> <td>Code</td>
> 
> <td>Station code. Repeated from input.</td>
> </tr>
> 
> <tr>
> <td>Lat</td>
> 
> <td>Latitude.</td>
> </tr>
> 
> <tr>
> <td>LineCode1</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV) served by this station.</td>
> </tr>
> 
> <tr>
> <td>LineCode2</td>
> 
> <td>Additional line served by this station. This is often the case
> when stations have multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center).</td>
> </tr>
> 
> <tr>
> <td>LineCode3</td>
> 
> <td>Similar to function as LineCodeX.</td>
> </tr>
> 
> <tr>
> <td>LineCode4</td>
> 
> <td>Similar to function as LineCodeX. Currently not in use.</td>
> </tr>
> 
> <tr>
> <td>Lon</td>
> 
> <td>Longitude.</td>
> </tr>
> 
> <tr>
> <td>Name</td>
> 
> <td>Station name.</td>
> </tr>
> 
> <tr>
> <td>StationTogether1</td>
> 
> <td>For stations with multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center), the additional
> StationCode will be listed here.</td>
> </tr>
> 
> <tr>
> <td>StationTogether2</td>
> 
> <td>Similar in function to StationTogether2. Currently not in
> use.</td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a name="Address">Address Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>City</td>
> 
> <td>City.</td>
> </tr>
> 
> <tr>
> <td>State</td>
> 
> <td>State (abbreviated).</td>
> </tr>
> 
> <tr>
> <td>Street</td>
> 
> <td>Street address (for GPS use).</td>
> </tr>
> 
> <tr>
> <td>Zip</td>
> 
> <td>Zip code.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `StationCode` - _required_ - Station code.  Use the Station List method to return a list of all station codes.
    Possible values: A01.

### JSON - Parking Information

> <h4 class="text-primary">Description</h4><br/>
> <br/>
> <p>Returns parking information at a station based on a given StationCode. Omit<br/>
> the StationCode to return parking information for all stations.</p><br/>
> <br/>
> <p>If a station has no parking, the StationsParking element will contain no<br/>
> child elements.</p><br/>
> <br/>
> <h4 class="text-primary">Response Elements</h4><br/>
> <br/>
> <table class="table table-condensed table-hover"><br/>
> <thead><br/>
> <tr><br/>
> <th class="col-md-3">Element</th><br/>
> <br/>
> <th>Description</th><br/>
> </tr><br/>
> </thead><br/>
> <br/>
> <tbody><br/>
> <tr><br/>
> <td>StationsParking</td><br/>
> <br/>
> <td><br/>
> Array containing station parking information (<a href=<br/>
> "#StationParking">StationParking</a>).<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="StationParking" name="StationParking">StationParking<br/>
> Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>Code</td><br/>
> <br/>
> <td>Station code. Useful when returning parking information for all<br/>
> stations. Use this value in other rail-related APIs to retrieve<br/>
> data about a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>Notes</td><br/>
> <br/>
> <td>When not NULL, provides additional parking resources such as<br/>
> nearby lots.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>AllDayParking</td><br/>
> <br/>
> <td><br/>
> Structure describing <a href="#AllDayParking">all-day<br/>
> parking</a> options.<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>ShortTermParking</td><br/>
> <br/>
> <td><br/>
> Structure describing <a href="#ShortTermParking">short-term<br/>
> parking</a> options.<br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="AllDayParking" name="AllDayParking">AllDayParking<br/>
> Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>TotalCount</td><br/>
> <br/>
> <td>Number of all-day parking spots available at a station.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>RiderCost</td><br/>
> <br/>
> <td>All-day cost per day (weekday) for Metro riders. NULL when no all-day<br/>
> spots are available. For most stations, this value is identical to<br/>
> the NonRiderCost.<br><br/>
> <br><br/>
> For cases where the NonRiderCost is different, the lower cost per<br/>
> day requires a valid rail trip using a SmarTrip&reg; card<br/>
> originating from a station other than the one where the patron<br/>
> parked. To receive this lower rate, patrons must pay for their<br/>
> parking with the same SmarTrip&reg; card used to enter/exit<br/>
> Metrorail, and must exit the parking lot within two hours of<br/>
> exiting Metrorail.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>NonRiderCost</td><br/>
> <br/>
> <td>All-day cost per day (weekday) for non-Metro riders. NULL when no all-day<br/>
> spots are available.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td colspan="2"><br/>
> <div class="text-primary" style="margin-top: 1em"><br/>
> <a id="ShortTermParking" name=<br/>
> "ShortTermParking">ShortTermParking Elements</a><br/>
> </div><br/>
> </td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SaturdayRiderCost</td><br/>
> <br/>
> <td>Similar to RiderCost, except denoting Saturday prices.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>SaturdayNonRiderCost</td><br/>
> <br/>
> <td>Similar to NonRiderCost, except denoting Saturday prices.</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>TotalCount</td><br/>
> <br/>
> <td>Number of short-term parking spots available at a station<br/>
> (parking meters).</td><br/>
> </tr><br/>
> <br/>
> <tr><br/>
> <td>Notes</td><br/>
> <br/>
> <td>Misc. information relating to short-term parking. NULL when no<br/>
> short-term spots are available.</td><br/>
> </tr><br/>
> </tbody><br/>
> </table>

#### Input Parameters
* `StationCode` - _optional_ - Station code.  Use the Station List method to return a list of all station codes.
    Possible values: E08, F06.

### JSON - Station Timings

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns opening and scheduled first/last train times based on a given
> StationCode. Omit the StationCode to return timing information for all
> stations.</p>
> 
> <p>Note that for stations with multiple platforms (e.g.: Metro Center, L'Enfant
> Plaza, etc.), a distinct call is required for each StationCode to retrieve the
> full set of train times at such stations.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>StationTimes</td>
> 
> <td>
> Array containing station timing information (<a href=
> "#StationTime">StationTime</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="StationTime" name="StationTime">StationTime
> Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Code</td>
> 
> <td>Station code for this station. Use this value in other
> rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td>StationName</td>
> 
> <td>Full name of the station.</td>
> </tr>
> 
> <tr>
> <td>*Day Elements</td>
> 
> <td>
> Container elements containing timing information based on
> <a href="#dow">day of the week.</a>
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="dow" name="dow">Monday/Tuesday/Wednesday/etc.
> Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>OpeningTime</td>
> 
> <td>Station opening time. Format is HH:mm.</td>
> </tr>
> 
> <tr>
> <td>FirstTrains</td>
> 
> <td>
> Structure containing <a href="#first">first train</a>
> information.
> </td>
> </tr>
> 
> <tr>
> <td>LastTrains</td>
> 
> <td>
> Structure containing <a href="#last">last train</a>
> information.
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="first" name="first">FirstTrains Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Time</td>
> 
> <td>First train leaves the station at this time. Format is
> HH:mm.</td>
> </tr>
> 
> <tr>
> <td>DestinationStation</td>
> 
> <td>Station code for the train's destination. Use this value in
> other rail-related APIs to retrieve data about a station.</td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="last" name="last">LastTrains Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Time</td>
> 
> <td>Last train leaves the station at this time. Format is HH:mm.
> Note that when the time is AM, it signifies the next day. For
> example, a value of 02:30 under a Saturday element means the last
> train leaves on Sunday at 2:30 AM.</td>
> </tr>
> 
> <tr>
> <td>DestinationStation</td>
> 
> <td>Station code for the train's destination. Use this value in
> other rail-related APIs to retrieve data about a station.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `StationCode` - _optional_ - Station code.  Use the Station List method to return a list of all station codes.
    Possible values: E10.

### JSON - Station List

> <h4 class="text-primary">Description</h4>
> 
> <p>Returns a list of station location and address information based on a given
> LineCode. Omit the LineCode to return all stations. The response is an array of
> objects identical to those returned in the Station Information method.</p>
> 
> <h4 class="text-primary">Response Elements</h4>
> 
> <table class="table table-condensed table-hover">
> <thead>
> <tr>
> <th class="col-md-3">Element</th>
> 
> <th>Description</th>
> </tr>
> </thead>
> 
> <tbody>
> <tr>
> <td>Stations</td>
> 
> <td>
> Array containing station information (<a href=
> "#Station">Station</a>).
> </td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="Station" name="Station">Station Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>Address</td>
> 
> <td>
> Structure describing <a href="#Address">address</a> information.
> </td>
> </tr>
> 
> <tr>
> <td>Code</td>
> 
> <td>Station code. Repeated from input.</td>
> </tr>
> 
> <tr>
> <td>Lat</td>
> 
> <td>Latitude.</td>
> </tr>
> 
> <tr>
> <td>LineCode1</td>
> 
> <td>Two-letter abbreviation for the line (e.g.: RD, BL, YL, OR, GR,
> or SV) served by this station.</td>
> </tr>
> 
> <tr>
> <td>LineCode2</td>
> 
> <td>Additional line served by this station. This is often the case
> when stations have multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center).</td>
> </tr>
> 
> <tr>
> <td>LineCode3</td>
> 
> <td>Similar to function as LineCodeX.</td>
> </tr>
> 
> <tr>
> <td>LineCode4</td>
> 
> <td>Similar to function as LineCodeX. Currently not in use.</td>
> </tr>
> 
> <tr>
> <td>Lon</td>
> 
> <td>Longitude.</td>
> </tr>
> 
> <tr>
> <td>Name</td>
> 
> <td>Station name.</td>
> </tr>
> 
> <tr>
> <td>StationTogether1</td>
> 
> <td>For stations with multiple platforms (e.g.: Gallery Place, Fort
> Totten, L'Enfant Plaza, and Metro Center), the additional
> StationCode will be listed here.</td>
> </tr>
> 
> <tr>
> <td>StationTogether2</td>
> 
> <td>Similar in function to StationTogether2. Currently not in
> use.</td>
> </tr>
> 
> <tr>
> <td colspan="2">
> <div class="text-primary" style="margin-top: 1em">
> <a id="Address" name="Address">Address Elements</a>
> </div>
> </td>
> </tr>
> 
> <tr>
> <td>City</td>
> 
> <td>City.</td>
> </tr>
> 
> <tr>
> <td>State</td>
> 
> <td>State (abbreviated).</td>
> </tr>
> 
> <tr>
> <td>Street</td>
> 
> <td>Street address (for GPS use).</td>
> </tr>
> 
> <tr>
> <td>Zip</td>
> 
> <td>Zip code.</td>
> </tr>
> </tbody>
> </table>

#### Input Parameters
* `LineCode` - _optional_ - Two-letter line code abbreviation:

<ul>
<li>RD - Red</li>
<li>YL - Yellow</li>
<li>GR - Green</li>
<li>BL - Blue</li>
<li>OR - Orange</li>
<li>SV - Silver</li>
</ul>
    Possible values: RD, YL, GR, BL, OR, SV.

## License

**flow**ground :- Telekom iPaaS / wmata-com-rail-station-connector<br/>
Copyright © 2019, [Deutsche Telekom AG](https://www.telekom.de)<br/>
contact: flowground@telekom.de

All files of this connector are licensed under the Apache 2.0 License. For details
see the file LICENSE on the toplevel directory.