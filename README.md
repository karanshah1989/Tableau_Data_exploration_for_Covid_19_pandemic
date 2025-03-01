# Tableau_Data_Exploration_for_Covid_19_pandemic
This repository has relevant information to Explore the information in SQL

# Global Infection Vs Vaccination Visualization in SQL (Part - 1)
<h3>This Portfolio is based upon the OurWorldInData Project done by MIT and Standford University.
</h3>
<p>In this Portfolio i have mentioned several Queries that are used to find View's of different Vies from diversed data-set of Covid19</p>
 
<!---->        

<!--<a href="" ><img src=""> </a>-->
 
</a>

<h2> About Me</h2>
<div>
<a href="[https://media-exp3.licdn.com/dms/image/D5635AQGENREQtSOVvA/profile-framedphoto-shrink_100_100/0/1624892028859?e=1626242400&v=beta&t=Vg9jbuG3OgWuTiinlR3A6Pdcpfw1iBu_MgY2_MlgNNE"><img src="https://media-exp3.licdn.com/dms/image/D5635AQGENREQtSOVvA/profile-framedphoto-shrink_100_100/0/1624892028859?e=1626242400&v=beta&t=Vg9jbuG3OgWuTiinlR3A6Pdcpfw1iBu_MgY2_MlgNNE](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYwkEAAAAAAFF16BjZalAeQxk?width=1936&height=1079)"></a>
</div>
<h3>
            KARAN SHAH
</h3>
<h4>
            Computer Engineer / Data Analyst / Pursuing Google Data Analytics Professional Certificate
</h4>
<h2> Portfolio Project (Part - 1)</h2>


<h4>Covid 19 Data Exploration</h4>


>Skills used: Joins, CTE's, Temp Tables, Windows Functions, Aggregate Functions, Creating Views, Converting Data Types

>Countries with Highest Infection Rate compared to Population
```
Select Location, Population, MAX(total_cases) as HighestInfectionCount,  Max((total_cases/population))*100 as PercentPopulationInfected
From PortfolioProject..CovidDeaths
--Where location like '%India%'
Group by Location, Population
order by PercentPopulationInfected desc
```


 **Output  for Table 1**
<a This image is of finding the total population affected by Covid-19 Infection href="https://1drv.ms/u/s!Agb9UJ70oAhYgYM2jDymgbEF5enhsA?e=soSt3C" ><img src="https://bn1305files.storage.live.com/y4mie76fSeaoaZCNJdy8S9kQK5osOk7g3LNVdlsEgjSmSy8zIw4oCw-PxRFIuo1kxYR7XbuRnHPgeZZDF7j4PMupEV2p_XQDo1NDqDrkgtvBdbK97e26hzv7RQNkoVFNYRp0SOUTom1OiMb8fBpObDxvH6u5EPA2jB8pTEfKIO-z1QlbFZN_7MglmNHk5RcAQ-_?width=1920&height=1080&cropmode=none"> </a>

>Countries with Highest Death Count per Population

```
Select Location, MAX(cast(Total_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%India%'
Where continent is not null 
Group by Location
order by TotalDeathCount desc

```
 **Output  for Table 2**
<a href="[https://1drv.ms/u/s!Agb9UJ70oAhYgYM2jDymgbEF5enhsA?e=soSt3C"><img src="https://bn1305files.storage.live.com/y4miNwsewCbNI2lI37AymFnY3rx3yIVORU_TIw8tnajx2yDfhzcHBvOQR9IgtUjIVmFlMmv1NtD4oimRmi3O2PqfVhUVvlXDEh74iG5pHpqHiHV9G-iwKfQd-zF64HMSgPU2GW40K6cFsAHFxS492q8LiWod4iIUFrBCb_QzgU-nmwYaIWmmOSj7JnlI8gD0U7F?width=1920&height=1080&cropmode=none](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYrkEAAAAAAEyBGZlB_yfAxJk?width=1920&height=1080)"> </a>     

>BREAKING THINGS DOWN BY CONTINENT
>Showing contintents with the highest death count per population
```
Select continent, MAX(cast(Total_deaths as int)) as TotalDeathCount
From PortfolioProject..CovidDeaths
--Where location like '%India%'
Where continent is not null 
Group by continent
order by TotalDeathCount desc
```
 **Output  for Table 3**
<a href="" ><img src="[https://bn1305files.storage.live.com/y4mbF8fTIS7OO9wGdgYc-61cNWQW6HWiqoapJaJ2yXsMDqhdNa2WC6VgXZtY0AedplbAGu9RUCFh6RlSrs4Tih2-9-vAl16_JGVAFDpvo8Tfh-PmUVJMiFCWnWcDwleR5ZbX87OsWrb4HEKCADakIl08OIGSJbzQKWorwf2HLtG1y51sttojCdQn43Zwkbraxvp?width=1920&height=1080&cropmode=none](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYr0EAAAAAAOEGN2cMNav69fc?width=1920&height=1080)"> </a>
>GLOBAL NUMBERS
```
Select SUM(new_cases) as total_cases, SUM(cast(new_deaths as int)) as total_deaths, SUM(cast(new_deaths as int))/SUM(New_Cases)*100 as DeathPercentage
From PortfolioProject..CovidDeaths
--Where location like '%India%'
where continent is not null 
--Group By date
order by 1,2

```
 **Output  for Table 4**
<a href="" ><img src="[https://bn1305files.storage.live.com/y4mPvYz1HtTLB6pWBpahWE3SEPwmFgII_X3Nbj9t75dcILGH6UvTRYsMA-G91M5fQfQyk1Tn8P0F7uxB8QfIVyZtEy_Xv0RDjo64eahSWq4p_Vwiwcj42WUdZfE6Og1-47Pwlq3pI3v5Hjm2CD5ofmo84QgtQZ7cwLvp-bHmjy1LZnjt7DH_15RABFx0qUVcMjj?width=1920&height=1080&cropmode=none](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYsEEAAAAAAE-VpMRXF66AR5w?width=1920&height=1080)"> </a>
>Total Population vs Vaccinations
>Shows Percentage of Population that has recieved at least one Covid Vaccine
```
Select dea.continent, dea.location, dea.date, dea.population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.Location Order by dea.location, dea.Date) as RollingPeopleVaccinated
--, (RollingPeopleVaccinated/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null 
order by 2,3
```
 **Output  for Table 5**
<a href="" ><img src="[https://bn1305files.storage.live.com/y4mwKC-Z-hcROzh0MqW28VBeOG-aNaY1XosfNcvl_FUCTAwN4iDTpnZ5Ker2P3WuUaSgAKfNLnMs24CTo_MWcTwNtwrKYIxaYfeNRTTY2bO2Q_4bGhkaPLUn8blz9LvV4F8k8RFlKQf8gtzYJQXcrSDXKkpqV99SsdnJTqvA154hIOXcvVwhqgLoO3NOKq2tRWf?width=1920&height=1080&cropmode=none](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYskEAAAAAAKQznklocYxgy14?width=1920&height=1080)"> </a>
>Using CTE to perform Calculation on Partition By in previous query
```
With PopvsVac (Continent, Location, Date, Population, New_Vaccinations, RollingPeopleVaccinated)
as
(
Select dea.continent, dea.location, dea.date, dea.population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.Location Order by dea.location, dea.Date) as RollingPeopleVaccinated
--, (RollingPeopleVaccinated/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null 
--order by 2,3
)
Select *, (RollingPeopleVaccinated/Population)*100
From PopvsVac

```
 **Output  for Table 6**
<a href="" ><img src="[https://bn1305files.storage.live.com/y4mwKC-Z-hcROzh0MqW28VBeOG-aNaY1XosfNcvl_FUCTAwN4iDTpnZ5Ker2P3WuUaSgAKfNLnMs24CTo_MWcTwNtwrKYIxaYfeNRTTY2bO2Q_4bGhkaPLUn8blz9LvV4F8k8RFlKQf8gtzYJQXcrSDXKkpqV99SsdnJTqvA154hIOXcvVwhqgLoO3NOKq2tRWf?width=1920&height=1080&cropmode=none](https://1drv.ms/i/c/5808a0f49e50fd06/IQQG_VCe9KAIIIBYsUEAAAAAARBGJN-9y6sKTYXv03aotow?width=1920&height=1080)"> </a>
>Using Temp Table to perform Calculation on Partition By in previous query
```
DROP Table if exists #PercentPopulationVaccinated
Create Table #PercentPopulationVaccinated
(
Continent nvarchar(255),
Location nvarchar(255),
Date datetime,
Population numeric,
New_vaccinations numeric,
RollingPeopleVaccinated numeric
)

Insert into #PercentPopulationVaccinated
Select dea.continent, dea.location, dea.date, dea.population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.Location Order by dea.location, dea.Date) as RollingPeopleVaccinated
--, (RollingPeopleVaccinated/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
--where dea.continent is not null 
--order by 2,3

Select *, (RollingPeopleVaccinated/Population)*100
From #PercentPopulationVaccinated
```
 **Output  for Table 7**
<a href="" ><img src="[https://bn1305files.storage.live.com/y4mtkNxu6-LqNlfEj019AIzWKHFEMAlHz2urc3lkfAoKR5BxaRYeuFtAVhbZb4SmqrHDR8uGu1KSIe9DtZRvPpJtBqcfo4Tsb-3mUdIfn_XpAhODOem1gVR2Q8tqdPGogKckIzIQxflolS3UN0SJto1uScebHIcF9ex9MTswWfZuo9YDspNWzl_8pNo_59NbZM7?width=1920&height=1080&cropmode=none](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYs0EAAAAAAJyeU9kKxgeiCyA?width=1920&height=1080)"> </a>

>Creating View to store data for later visualizations
```
Create View PercentPopulationVaccinated as
Select dea.continent, dea.location, dea.date, dea.population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.Location Order by dea.location, dea.Date) as RollingPeopleVaccinated
--, (RollingPeopleVaccinated/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null 
```
 **Output  for Table 8**
<a href="" ><img src="[https://bn1305files.storage.live.com/y4mQx8kwUXbtgn9gEKaPX0ggbl3PvOD_-3bgFhAZ15XMddkvWyxgsjyYjmWtfYfHZuqsZs5M0hRNXVnsFFFUSL9pk4lctNoIqNjl8NAuu0e0ewiPavG4_0azhU40PxP1SM6yffA-FXgoQaakDvPJP20MJGxezDBnt7hevuPWy_TThPkuQ5wyOTJ22EwBzZWjScg?width=1920&height=1080](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYtUEAAAAAAGRM2YYAWQyxs_Y?width=1920&height=1080](https://1drv.ms/i/c/5808a0f49e50fd06/UQQG_VCe9KAIIIBYtUEAAAAAAGRM2YYAWQyxs_Y?width=1920&height=1080)"> </a>


