
### Bars

.es(index='dccrime',timefield='ReportDate',split=Offense:8).movingaverage(50).range(0,100).bars(2)

### Show derivative

`.es(index='dccrime',timefield='ReportDate').derivative().mvavg(10)`

.es(index='dccrime',timefield='ReportDate',split=Offense:8).derivative().mvavg(40)

### Show correlation

`(.es(index='dccrime',timefield='ReportDate'),.es(index='weather',timefield='Date',metric='sum:MeanTemp')).mvavg(10).range(0,100)`

Rain

.es(index='dccrime',timefield='ReportDate').movingaverage(10).label(Offense), .es(index='weather',timefield='Date',metric='sum:MeanTemp').movingaverage(10).label(MeanTemp).title(All_Crime),.es(index='weather',timefield='Date',metric='sum:Precipitation').label(Rain).yaxis(2)




