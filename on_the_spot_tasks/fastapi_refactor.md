Необходимо сделать рефакторинг кода:
=================================


``` python
from team_project.strategies import container as strategieS_container
from team_project.schemas import ScorePlayload
from team_project.exceptions import Error404
from fastapi import Request
@app.put('/strategies/<strategy>')
def get_strategy(strategy, request):
    if strategies_container.has(strategy):
        strategy = strategies_container.get(strategy)
    else:
        error = 'Неизвестное имя стратегии: ' + strategy
        raise Error404(error) # raise 404

    try:
        payload = await request.json()
    except BaseException:
        error = 'payload get error'
        raise Error404(error) # raise 404

    if ScorePlayload().is_valid(payload):
        pass
    else:
        msg = 'Input payload validation failed'
        return response.bad_request(msg, data=payload)

    score = strategy.get_score(payload)

    return response.ok(data=score.normalize().to_dict())

@app.post('/strategies/<strategy>', methods=['DELETE'])
def post_strategy(strategy):
    if strategies_container.has(strategy):
        strategy = strategies_container.get(strategy)
    else:
        error = 'Неизвестное имя стратегии: ' + strategy
        raise Error404(error) # raise 404



    strategies_container.remove(strategy)

    return response.ok()
 ```
